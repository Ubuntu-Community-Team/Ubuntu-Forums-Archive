---
title: "Problems with last.fm/rythmbox on dell mini"
date: 2009-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by charlie651 on 2009-03-04
Hi, I am new to linux but i just got the dell mini 9 with ubuntu and a 4gb ssd.  I and am trying to set it up. I really want to get the last.fm player working to play music because of the limeted space on the ssd.  
I have installed the last.fm client by going into the terminal and using 'sudo apt-get install lastfm'

it seems to have installed fine, it shows up in my menus and everything, but when i run it i get a message,
"Couldn't load radio service 'httpinput'. The radio will not work."
and i cant get it to play any music.

I have looked this up and it seems like some other people have had this problem, and solved it by finding fixing broken library links but i am not sure how to do this... here is the the thread on the last.fm forum i was looking at 
[http://www.last.fm/forum/34905/_/365911](http://www.last.fm/forum/34905/_/365911)

The laptop also has rhthmbox installed, and this is also unable to play last.fm through the plugin!..

Has anyone else got this to work on ubuntu? Anyone had this problem? Any idea how to fix it?

my mini 9 is running ubuntu 8.04.

Thanks!

also here is the log from /home/charlie/.local/share/Last.fm/Last.fm.log

i checked to make sure that /usr/lib/lastfm/libserv_httpinput.so was there and it does exist


90304 02:19:25 - 3062531904 - Init(164) - L1
************************************* STARTUP ********************************************

090304 02:19:25 - 3062531904 - Init(165) - L1
OS: Unix/Linux

090304 02:19:25 - 3062531904 - Init(172) - L2
No default message handler found, using our own.

090304 02:19:25 - 3062531904 - initLogger(338) - L1
App version: 1.4.2.58240

090304 02:19:25 - 3062531904 - setLanguage(368) - L3
Setting language to: en

090304 02:19:25 - 3062531904 - WebService(39) - L3
Initialising Web Service

"090304 02:19:25" - "-1232435392" - void WebService::autoDetectProxy() ( 187 ) - L4


"090304 02:19:25" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
"Proxy Test" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

"090304 02:19:25" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
"Proxy Test" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

090304 02:19:25 - 3060984720 - OpenSocket(418) - L3
Listener bound to port 33367

"090304 02:19:25" - "-1242375280" - QObject* AudioControllerThread::loadPlugin(QString) ( 197 ) - L4
"/usr/lib/lastfm/libsrv_httpinput.so"

090304 02:19:25 - 3062531904 - resetWidget(357) - L3
Launching login dialog mode CHANGE_PASS

"090304 02:19:26" - "-1232435392" - MetaDataWidget::MetaDataWidget(QWidget*) ( 100 ) - L4
Detected default: "Sans Serif,9,-1,5,50,0,0,0,0,0"

"090304 02:19:26" - "-1232435392" - void Container::setupTrayIcon() ( 241 ) - L4


090304 02:19:26 - 3062531904 - LoadIcons(153) - L4
Icons loaded

"090304 02:19:26" - "-1232435392" - void Container::updateAppearance() ( 1142 ) - L4


090304 02:19:26 - 3062531904 - stop(735) - L4
AudioController requesting stop of

090304 02:19:26 - 3062531904 - setState(907) - L4
AudioController state: State_Stopping

"090304 02:19:26" - "-1232435392" - void Container::updateUserStuff(LastFmUserSettings&) ( 1120 ) - L4


"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"Friends" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/friends.xml?imagesize=small"

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"Neighbours" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/neighbours.xml?imagesize=small"

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"UserTags" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/tags.xml"

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"RecentTracksRequest" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recenttracks.xml"

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"RecentlyLovedTracks" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recentlovedtracks.xml"

"090304 02:19:26" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
"UserPictures" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"RecentlyBannedTracks" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recentbannedtracks.xml"

090304 02:19:26 - 3062531904 - stop(483) - L3
Stopping radio

090304 02:19:26 - 3062531904 - setState(667) - L4
Radio state: State_Stopped

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
"Handshake" initiated: "ws.audioscrobbler.com/radio/handshake.php?version=1.4.2.58240&platform=linux&p latformversion=Unix%2FLinux&username=Charlie651&pa sswordmd5=1799432518ec7132b60dd026816ad048&languag e=en"

090304 02:19:26 - 3062531904 - setState(667) - L4
Radio state: State_Handshaking

"090304 02:19:26" - "-1232435392" - void ScrobblerManager::handshake(const Scrobbler::Init&) ( 76 ) - L4
"Charlie651"

"090304 02:19:26" - "-1232435392" - Scrobbler::Scrobbler(const Scrobbler::Init&) ( 502 ) - L4
Initiating Scrobbler handshake for: "Charlie651"

"090304 02:19:26" - "-1232435392" - virtual void ScrobblerHandshakeRequest::request() ( 842 ) - L4
GET: "?hs=true&p=1.2&c=***&v=1.4.2.58240&u=Charlie651&t =1236133166&a=e1a8c002306829e0f06ce44dc004db46"

Waiting on CachedHttpJanitor thread!

Waiting on CachedHttpJanitor finished!

"090304 02:19:27" - "-1232435392" - QWidget* mainWindow() ( 36 ) - L4
(Container(0x8210268, name = "MainWindow") , ShareDialog(0x8211810, name = "ShareDialog") , SettingsDialog(0x8255d90, name = "SettingsDialog") , QMenu(0xb37c6090) , DiagnosticsDialog(0x82f3a20, name = "DiagnosticsDialog") , QMenu(0x83fc1c0) , QMenu(0x83e9078, name = "menuFile") , QMenu(0x83e8e98, name = "menuView") , QMenu(0x83ea0a8, name = "menuControls") , QMenu(0x83e7f00, name = "menuHelp") , QMenu(0x83ea520, name = "menuUser") , QMenu(0x83eabd8, name = "menuTools") , QLabel(0x8428470) , QComboBoxPrivateContainer(0x824f718) , QComboBoxPrivateContainer(0x82f67c0) , QComboBoxPrivateContainer(0x8253cc8) , QComboBoxPrivateContainer(0x822d780) )

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Proxy Test" response: 302

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"Proxy Test" request succeeded

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recenttracks.xml"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"RecentTracksRequest" response: 302

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"RecentTracksRequest" request succeeded

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/neighbours.xml?imagesize=small"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Neighbours" response: 302

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Proxy Test" response: 302

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/tags.xml"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"UserTags" response: 302

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"UserPictures" response: 302

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/radio/handshake.php?version=1.4.2.58240&platform=linux&p latformversion=Unix/Linux&username=Charlie651&passwordmd5=1799432518ec 7132b60dd026816ad048&language=en"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Handshake" response: 302

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"Proxy Test" request succeeded

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"UserTags" request succeeded

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"UserPictures" request succeeded

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"Handshake" request succeeded

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/friends.xml?imagesize=small"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Friends" response: 302

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recentbannedtracks.xml"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"RecentlyBannedTracks" response: 302

090304 02:19:27 - 3062531904 - setState(667) - L4
Radio state: State_Uninitialised

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"Friends" request succeeded

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"RecentlyBannedTracks" request succeeded

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recentlovedtracks.xml"

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"RecentlyLovedTracks" response: 302

090304 02:19:27 - 3062531904 - onRadioError(883) - L2
Radio error 4: The Last.fm servers are temporarily overloaded, please try again in a moment.

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"RecentlyLovedTracks" request succeeded

Http request returned redirect (301, 302 or 307): "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://post.audioscrobbler.com/?hs=true&p=1.2&c=***&v=1.4.2.58240&u=Charlie651&t= 1236133166&a=e1a8c002306829e0f06ce44dc004db46"

"090304 02:19:27" - "-1232435392" - void Scrobbler::hardFailure() ( 523 ) - L4
Scrobbler HTTP error: 49

"090304 02:19:27" - "-1232435392" - void Scrobbler::hardFailure() ( 537 ) - L4
Scrobbler hard failure. Retrying in 30 seconds.

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
"Neighbours" response: 200

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
"Neighbours" request succeeded

090304 02:19:37 - 3062531904 - onRadioError(883) - L2
Radio error 1009: Couldn't load radio service 'httpinput'. The radio will not work.

---

### Post by sirebral on 2009-03-05
I tested this out a little.  I cannot get the radio to work either.  It might be a problem with GStreamer.  That is an error I returned.  It might also be a problem with Rythmbox, not likely since it is universal.

The last.fm plugin on my desktop works, but that is using 8.10.  I've tried different sound settings. Rythmbox on the DELL Mini 9 looks different then on 8.10 when you are changing settings.  Probably a space saver, but I would like the stuff back.

I thought I would help.  I am just not sure how too.  Good luck!!  I just signed up for Last.fm and it was worth it.

---

### Post by charlie651 on 2009-03-05
Hey, thanks for trying.. I might just try installing 8.10 on my mini if it will get last fm working.  I just have the 4gb ssd and can't fit any music on there so need to get it or something similar working.. 

and yeah, glad you got turned on to last.fm, i think it is totally worth it and gives way better reccomendations than pandora.

---

### Post by pipposanta on 2009-03-06
interested too...
rhytmbox plugin and lastfm app don't work also on my 8.04 mini 9.
I have a 8 gb ssd so i can't put a lot of music into.

---

### Post by sugarland2k on 2009-03-18
I had the same issue on my Mini 9 with Ubuntu 8.04.01 and Last.fm.  Working on this issue and I will advise the thread..

---

### Post by chriscl on 2009-03-26
For what it is worth...

I couldn't get the Last.fm radio working either, but Rhythmbox does let me log in, (set it up from the "plugins" menu entry) and it does appear to be submitting tracks I play in Rhythmbox to Last.fm?

---

### Post by dragonmojo on 2009-03-27
I am using Rhythmbox on my Mini9 with Ibex 8.10 installed. I am able to play my music collection, as well as receive internet radio (listening to a UK station right now).

I am familiar with last.fm, having used it on my desktop. I will test it out on my Mini9 and see what happens.

btw, I do not keep any of my mp3s on the SSD. They're all on the 8Mb SDHC card, which I prefer to do, and they play fine.

---

### Post by taylork on 2009-03-29
It also doesn't work for me (default 8.04 && rythmbox && dell mini 9 && last.fm).

In the meantime, the vagalume app is great for last.fm, It's more of a maemo app (i.e. for a Nokia N800) but the gtk version works fine too. It's part of the official repository in 8.10 & 9.04 but you can install from their own repository:

[http://vagalume.igalia.com/files/ubuntu/hardy/vagalume_0.7.1-0hardy1_i386.deb]("http://vagalume.igalia.com/files/ubuntu/hardy/vagalume_0.7.1-0hardy1_i386.deb")

[http://vagalume.igalia.com/]("http://vagalume.igalia.com/")


-------------

Also, to the storage issue posts ... consider using an SD card to store videos/songs ...

---

### Post by dorkmo on 2009-03-29
ive been using [seeqpod.com]("http://www.seeqpod.com")

its nice but doesnt fit on the small screen quite right

---

### Post by sirebral on 2009-03-29
After I made the switch to 8.10 Last.FM worked for me.

---

