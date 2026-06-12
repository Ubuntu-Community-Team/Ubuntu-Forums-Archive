---
title: "Re: Deluge keeps crashing"
date: 2009-05-01
forum: General Help
---

### Post by robbiej on 2009-05-01
Re: Deluge keeps crashing
This is what I got when it crashed.



drobert@robert-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentCreator
Initialising plugin NetworkGraph
Initialising plugin WebSeed
Initialising plugin Search
Initialising plugin TorrentPeers
Initialising plugin SpeedLimiter
Initialising plugin TorrentNotification
Initialising plugin WebUi
Initialising plugin BlocklistImport
Initialising plugin TorrentFiles
Initialising plugin MoveTorrent
Initialising plugin FlexRSS
Initialising plugin DesiredRatio
Initialising plugin NetworkHealth
Initialising plugin EventLogging
Initialising plugin Scheduler
Applying preferences
Starting DHT...
Showing window
Found TorrentSearch plugin...
Found TorrentFiles plugin...
Found TorrentPeers plugin...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
save uploaded memory
Pickling state...
Segmentation fault
robert@robert-desktop:~$

---

### Post by lovinglinux on 2009-05-01
First of all would be nice if you could provide more info, like which Ubuntu and Deluge versions you are using.

From the output, it seems that you are using the old Deluge version, 0.5.x. Please confirm that. If you are using Deluge 0.5.x, you could try deleting the contents of ~/.config/deluge and restart it. Please notice that this will delete your current settings and probably your list of .torrent files, but probably not the downloaded content.

Alternatively, you could try installing a newer version, like 1.1.7 from [here](http://dev.deluge-torrent.org/wiki/Download).

If you are already using a version from the 1.x.x series, then I would suggest removing your plugins, because they are incompatible with newer versions and could be the cause of the problem (just guessing).

---

### Post by robbiej on 2009-05-01
Hi, I am using ubuntu 8.10. and deluge 0.5.9.3. I will try installing a newer version, thanks for your help.

---

