---
title: "Just a sily cuestion"
date: 2009-03-27
forum: General Help
---

### Post by B4RR13N705 on 2009-03-27
Hi, im downloading a lot of stuff with deluge bittorrent client (pretty nice software :) ) 
Whan you open it you can see the window, if you close the windows deluge still works on the background, you can see it on the notification area.
I want to auto-execute deluge when i turn the pc on, the problem is that the window appears, i want to start it but i want it to run directly from de background, you know what i mean. :KS:KS

---

### Post by ad_267 on 2009-03-27
Run "transmission -m" which will run transmission minimised in the system tray. You can run "transmission --help" or "man transmission" to see more options.

---

### Post by lovinglinux on 2009-03-27
I guess you can do this with command-line. I never tried, but you can find more info about at [http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

### Post by mb_webguy on 2009-03-27
The newest version of Deluge (available from the [Deluge website]("http://deluge-torrent.org/") or the [Deluge PPA]("https://launchpad.net/~deluge-team/+archive/ppa")) has a "Start in tray" option in Preferences->Interface.  So if you check this option, and add Deluge to your System->Preferences->Sessions->Startup Programs, it will start when you login, and automatically start minimized to the notification area.

---

### Post by B4RR13N705 on 2009-03-27
Thanx, it worked! :popcorn:

---

