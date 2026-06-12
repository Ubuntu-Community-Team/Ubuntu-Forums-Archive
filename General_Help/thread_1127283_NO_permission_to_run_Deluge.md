---
title: "NO permission to run Deluge"
date: 2009-04-16
forum: General Help
---

### Post by mibadt on 2009-04-16
Hi,
I'm on a fully updated Kubuntu 8.10 PC.
Using Adept, I successfully installed Deluge, and initially could run it. I (only) modified the torrent port and tried to restart the application (for the change to take effect). Unfortunately, now I can't launch Deluge any more. Reboot didn't help either. 
Trying to run deluge from within the terminal I got the response detailed below, claiming "Permission denied".

Please advise how can I run Deluge (with my preferred port).

Thanks up front!

Michael Badt

-----copy of terminal------
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin Scheduler
Initialising plugin EventLogging
Initialising plugin NetworkHealth
Initialising plugin SpeedLimiter
Initialising plugin DesiredRatio
Initialising plugin Search
Initialising plugin MoveTorrent
Initialising plugin TorrentPeers
Initialising plugin WebUi
Initialising plugin BlocklistImport
Initialising plugin FlexRSS
Initialising plugin WebSeed
Initialising plugin TorrentFiles
Initialising plugin TorrentNotification
Initialising plugin TorrentCreator
Initialising plugin NetworkGraph
Applying preferences
Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Permission denied
Aborted

---

