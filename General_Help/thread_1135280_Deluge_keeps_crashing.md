---
title: "Deluge keeps crashing"
date: 2009-04-24
forum: General Help
---

### Post by robbiej on 2009-04-24
Deluge loads up ok and I leave it for a few hours or so and when I come back to it its gone. This always happens when I leave it for a long time.

Wondered if anyone can help because its really annoying.

many thanks,

rob.

---

### Post by Bender2k14 on 2009-04-24
What version of Ubuntu are using?

---

### Post by robbiej on 2009-04-24
Im using 8.10.

---

### Post by prem1er on 2009-04-24
Open Deluge from the terminal.  When it crashes post the errors back here.  Are you out of disc space by any chance?

---

### Post by robbiej on 2009-04-24
it has like 65GB left. Sorry im new to ubuntu, what command should i use?

---

### Post by prem1er on 2009-04-24
```
deluge
```

In terminal.

---

### Post by robbiej on 2009-04-28
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

