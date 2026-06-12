---
title: "deluge problem"
date: 2009-03-22
forum: General Help
---

### Post by numbness05 on 2009-03-22
Hey people, went to open deluge the other day and it appears that it no longer wishes to open...
Some one suggested opening it in a terminal and posting the outcome on here...so can any one see anything odd with the following, something that would prevent it from opening

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
self.tab_details.update(unique_id)daniel@daniel-desktop:~$ deluge
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

File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 170, in update
self.paint_customprogress()
File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 82, in paint_customprogress
gc = progress_window.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'

Thank you any advice would be very much appreciated 

Kind regards :p

---

### Post by Graduate on 2009-05-11
> rm -r /home/usuario/.config/deluge 

I had the same problem and I ran this. Your files and progress will be deleted! But deluge will be able to start over again.

---

