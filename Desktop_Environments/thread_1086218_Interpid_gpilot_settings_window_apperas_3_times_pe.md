---
title: "Interpid gpilot settings window apperas 3 times per sync"
date: 2009-03-03
forum: Desktop Environments
---

### Post by hurt138 on 2009-03-03
Every time I sync my Palm Treo 755p via usb it will open the settings window for gpilot ("gnome-pilot settings").

It will open it once when it first makes the connection, another time when it is sync'ing, and a 3rd time after it has finished sync'ing. Leaving them open does not make it stop from opening it three times.

Everything seems to be syncing fine and it works as it was before upgrading to Interpid, but it is the minor annoyance of the setting window poping up server times every sync.

I have tried some trouble shooting of my own and restarting gpilot fresh does not fix the issue, turning off all the sync options (todo, calendar, memos, etc) does not help. I have even tried syncing in Jpilot and it will still open the settings windows. I am pretty sure Jpilot uses gpilot to actually talk to the Palm, so I believe it is to be a gpilot issue and not evolution.

** Versions **
gnome-pilot applet 2.0.15
Ubuntu 8.10 the Intrepid Ibex
Evolution 2.24.3

Anyone else having this issue, or seeing a similar thing happen?

---

### Post by sgosnell on 2009-03-03
No, JPilot does not use any part of gnome for syncing, it has its own sync.  If the gsync stuff is opening, then you're not syncing with jpilot.  You have to manually start the JPIlot sync daemon every time, by clicking on the hotsync icon in JPilot before you start the sync.  That will override the gpilot daemon.  I don't often sync to gpilot, so I can't offer much help there.  JPilot is far superior IMO, and it has the desktop component for Keyring, which is essential for me.

---

### Post by hurt138 on 2009-03-04
Perhaps this is a Gnome or Hal issue then?

I can kill all running processes for gpilot and running a sync in jpilot still pops up the gnome-pilot settings window 3 times. looking in a ps aux again while the sync was running show gpilot was started again. Jpilot still runs and syncs fine.

Jpilot is nice if you want the classic Palm application feel, but I am a fan of syncing with evolution. Allows shared calendars, and loads of other features.

---

### Post by hurt138 on 2009-03-04
Problem Solved!

System -> Preferences -> Removable Drives and Media 

 select the PDA's Tab.

 Uncheck sync on connection.

 Now just press the sync button when your pda is connected and it will not keep poping up the settings window.

I am guessing the palm makes and disconnects several times during the sync operation and each time it loads the settings window when this is checked.

---

