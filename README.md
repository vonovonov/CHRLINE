# LINE DemoS Bot - CHRLINE API

>What is CHRLINE?\
>It is LINE Chrome API, just for debug

>If you can help update this project, \
Welcome join our [Discord](https://discord.gg/vQrMbjA)

## About Project
This project is for debug only, because it does not use thrift

So I don’t recommend you to use this to run the bot, even if it has many functions

## What can it do?
If you have a certain degree of understanding of Line thrift, then you must have heard of **TMoreCompact** \
But for most people, it is difficult to decompile TMoreCompact, even if it has lower confusion in some version \
But if you can use this project to understand the differences in LINE thrift
\

## TMoreCompactProtocol
We added the simple function of TMoreCompact for the [first time on 26 May](https://github.com/DeachSword/CHRLINE/commit/3192377714730ddf83208836661182d641d21cb0) \
And added TMoreCompact to [the development version at Jul 8](https://github.com/DeachSword/CHRLINE/commit/d7d8430e74417a06c9ad159a5675b7787ec75c54) \
It's based on the thrift of the LINE Android version \
Its purpose is to effectively compress mid (32 bytes) to 16 bytes



####  Example
```
from CHRLINE import *

cl = CHRLINE() # login

print('/S3 - len: %s' % len(cl.testTBinary()))
print('/S4 - len: %s' % len(cl.testTCompact()))
print('/S5 - len: %s' % len(cl.testTMoreCompact()))
```
####  Result
```
> /S3 - len: 576
> /S4 - len: 528
> /S5 - len: 496
```
This shows that TMoreCompact has the best compression\
If you want to write TMoreCompact, only need to sniff results and reverse engineer

####  Requirement
- Python 3.6
    - pycrypto
    - pycryptodemo
    - xxhash
    - httpx[http2]
    - gevent

## Function overview
- E2EE SQR Login
- Email Login
- Services
    - TalkService
        - getEncryptedIdentity
        - getContact
        - getContacts
        - getGroup
        - getGroups
        - getGroupsV2
        - getCompactGroup
        - getChats
        - sendMessage
            - sendContact
            - sendLocation
        - getGroupIdsJoined
        - getGroupIdsInvited
        - getAllContactIds
        - getBlockedContactIds
        - getBlockedRecommendationIds
        - getAllReadMessageOps
        - getLastOpRevision
        - getServerTime
        - getConfigurations
        - fetchOps
        - deleteOtherFromChat
        - cancelChatInvitation
        - acceptChatInvitation
        - getContactsV2
        - acceptChatInvitationByTicket
        - getPreviousMessagesV2WithRequest
        - sendChatChecked
        - unsendMessage
        - findAndAddContactsByMid
        - inviteIntoChat
        - deleteSelfFromChat
        - findChatByTicket
        - updateChat
        - sendPostback
        - wakeUpLongPolling
        - getMessageBoxes
        - getMessageReadRange
        - getChatRoomAnnouncementsBulk
        - removeChatRoomAnnouncement
        - fetchOperations
        - unblockContact
        - blockContact
        - acquireEncryptedAccessToken
        - getCountries
        - createRoomV2
        - createChatRoomAnnouncement
        - getAllChatMids
        - reissueChatTicket
        - sendEchoPush
        - getRepairElements
        - getSettingsAttributes2
        - updateSettingsAttributes2
        - rejectChatInvitation
        - updateProfileAttribute
        - negotiateE2EEPublicKey
        - react
        - getE2EEPublicKeys
        - createChat
        - updateRegion
        - getChatExistence
        - getChatMembership
        - setChatHiddenStatus
        - getReadMessageOps
        - getReadMessageOpsInBulk
        - getE2EEMessageInfo
        - getMessageBoxCompactWrapUpList
        - getRecentMessages
        - getRecentMessagesV2
        - getPreviousMessageIds
        - getMessagesByIds
        - getMessageBoxesByIds
        - getMessageBoxCompactWrapUpListV2
        - getPreviousMessagesV2
        - getPreviousMessagesV2WithReadCount
        - getNextMessagesV2
        - getAllRoomIds
        - getCompactRooms
        - acquireCallTicket
        - isAbusive
        - removeBuddySubscriptionAndNotifyBuddyUnregistered
        - makeUserAddMyselfAsContact
        - getFollowers
        - getFollowings
        - removeFollower
        - follow
        - unfollow
        - bulkFollow
        - decryptFollowEMid
        - getChatRoomBGMs
        - updateChatRoomBGM
        - addSnsId
        - removeSnsId
        - getContactRegistration
        - getHiddenContactMids
        - blockRecommendation
        - unblockRecommendation
        - getRecommendationIds
        - sync (DIED)
        - reissueTrackingTicket
    - AccessTokenRefreshService
        - refreshAccessToken
    - AuthService
        - openAuthSession
        - getAuthRSAKey
        - setIdentifier
        - updateIdentifier
        - resendIdentifierConfirmation
        - confirmIdentifier
        - removeIdentifier
        - getClovaAppToken
        - loginFromClova
        - validateClovaRequest
        - setClovaCredential
        - validateClovaAppToken
    - BuddyService
        - getPromotedBuddyContacts
    - CallService
        - acquireCallRoute
        - acquireOACallRoute
        - searchPaidCallUserRate
        - acquirePaidCallCurrencyExchangeRate
        - lookupPaidCall
        - acquirePaidCallRoute
        - getPaidCallBalanceList
        - getPaidCallHistory
        - getCallCreditProducts
        - reserveCallCreditPurchase
        - getCallCreditPurchaseHistory
        - redeemPaidCallVoucher
        - getPaidCallMetadata
        - acquireGroupCallRoute
        - getGroupCall
        - inviteIntoGroupCall
        - markPaidCallAd
        - getPaidCallAdStatus
        - acquireTestCallRoute
        - getGroupCallUrls
        - createGroupCallUrl
        - deleteGroupCallUrl
        - updateGroupCallUrl
        - getGroupCallUrlInfo
        - joinChatByCallUrl
    - ChannelService
        - issueChannelToken
        - approveChannelAndIssueChannelToken
        - getChannelInfo
        - getCommonDomains
        - issueRequestTokenWithAuthScheme
        - getReturnUrlWithRequestTokenForAutoLogin
    - LiffService
        - issueLiffView
        - getLiffViewWithoutUserContext
        - issueSubLiffView
    - PrimaryAccountInitService
        - openPrimarySession
        - getCountryInfo
        - getPhoneVerifMethod
        - sendPinCodeForPhone
        - verifyPhone
        - validateProfile
        - exchangeEncryptionKey
        - setPassword
        - registerPrimaryUsingPhone
    - SearchService (WIP)
        - searchAll
        - searchCollection
        - searchLineat
        - searchByPopularCategory
        - searchByCategory
        - getPopularCategory
        - getNotice
        - getSearchSection
        - getAutocomplete
    - SettingsService
        - getSetting
        - contextAgnosticGetSetting
        - setSetting
        - setSettingWithScope
        - resetSetting
        - searchSettings
        - contextAgnosticSearchSettings
    - ShopAuthService
        - establishE2EESession
    - ShopService
        - getProduct
        - getProductsByAuthor
        - getStudentInformation
        - canReceivePresent
        - getOwnedProductSummaries
    - SquareService
        - inviteIntoSquareChat
        - inviteToSquare
        - getJoinedSquares
        - markAsRead
        - reactToMessage
        - findSquareByInvitationTicket
        - fetchMyEvents
        - sendSquareMessage (text only)
        - fetchSquareChatEvents
        - getSquare
        - getJoinableSquareChats
    - SquareBotService
        - getSquareBot
    - ObsService
        - forwardObjectMsg
        - trainingImage
        - updateProfileImage
        - updateProfileCover
        - uploadObjHome
        - uploadObjTalk
        - uploadMultipleImageToTalk
    - TimelineService
        - MyHome
            - getProfileCoverDetail
            - updateProfileCoverById
            - sendContactV2
            - getProfileDetail
            - getTimelintTab
        - Post
            - getPost
            - createComment
            - deleteComment
            - listComment
            - createLike
            - cancelLike
            - listLike
            - searchNote
            - sendPostToTalk
            - getHashtagPosts
            - getHashtagSuggest
            - getHashtagPopular
            - getTimelineUrl
            - getPostShareLink
            - getDiscoverRecommendFeeds
            - updateProfileCoverById2
            - getOACarousel
            - getPartlyBlockContacts
            - getClosedContacts
            - getHideContacts
            - getAutoOpenOption
            - getHideGrouphomeList
            - getNewpostStatus
            - getGroupProfileimageList
            - getUserProfile
            - getUserPopupDetail
            - syncBuddygroup
        - Album
            - changeGroupAlbumName
            - deleteGroupAlbum
            - addImageToAlbum
            - getAlbumImages
            - deleteAlbumImages
        - Story (WIP)
            - uploadStoryObject (WIP)
            - createStoryContent (WIP)
            - getRecentstoryStory
            - sendMessageForStoryAuthor
        - Search
            - Search
        - Keep
            - syncKeep
    - CubeService (beta)
        - issueBillSplitId
        - getBillSplitShareLink
        - getBillSplitSurvey
        - putBillSplitBills (test)
        - snedBillSplitBills
    - Others
        - returnTicket (test)
        - getModulesV2
        - openSession
        - connectEapAccount
        - verifyEapLogin
        - getCountrySettingV4
        - getRSAKeyInfo
        - loginZ
        - loginV2 (WIP)

