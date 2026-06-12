---
title: "Deluge not opening..."
date: 2009-03-19
forum: General Help
---

### Post by numbness05 on 2009-03-19
Hey there people..

Any ideas any one, Deluge used to open up fine and I was in the middle of downloading a couple of videos.
I came back to it after having my PC switched off for the evening and it doesn't appear to want to open it will start the process of opening it in the bottom panel but then promptly changes its mind and doesn't complete the opening process..

I have since switched to using Transmission which seems to work just as well if not better but I still want to beable to finish downloading the items I have had running in deluge for some time now and don't really want to have to start from scratch.

Does any body have any idea what maybe causing this problem all of a sudden?

Many many thanks in advance
Kind regards 
Numbness ;)

---

### Post by PurposeOfReason on 2009-03-19
Run deluge in a terminal and post the output, please.

---

### Post by numbness05 on 2009-03-20
Hey sorry to be a pain...
What is the command I should use to open in the terminal (sorry my understanding of Linux is very limited)

Many thanks once again. :D

---

### Post by whitethorn on 2009-03-20
Go to Applications -> Accessories -> Terminal   

then type

deluge

post what comes up in here.

---

### Post by numbness05 on 2009-03-21
daniel@daniel-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin Scheduler
Initialising plugin Search
Initialising plugin NetworkHealth
Initialising plugin DesiredRatio
Initialising plugin FlexRSS
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin MoveTorrent
Initialising plugin TorrentCreator
Initialising plugin SpeedLimiter
Initialising plugin TorrentNotification
Initialising plugin TorrentFiles
Initialising plugin NetworkGraph
Initialising plugin WebUi
Initialising plugin WebSeed
Applying preferences
Starting DHT...
Showing window
Traceback (most recent call last):
  File "/usr/bin/deluge", line 132, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 116, in start_deluge
    interface.start(get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1034, in start
    self.update()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1213, in update
    self.update_torrent_info_widget()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1287, in update_torrent_info_widget
    self.tab_details.update(unique_id)
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 170, in update
    self.paint_customprogress()
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 82, in paint_customprogress
    gc = progress_window.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'



Hope that is of some use my friend....  It means nothing to me.

Thanks again!

---

