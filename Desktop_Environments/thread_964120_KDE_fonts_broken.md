---
title: "KDE fonts broken"
date: 2008-10-30
forum: Desktop Environments
---

### Post by caitifty on 2008-10-30
Hi all

I have a server with applications displaying over X to a remote laptop.  All gnome applications work fine, but all KDE applications I've tried have fonts displayed so tiny I can't see them.  I've tried using kcontrol to fix the problem, but as you can't read the labels in kcontrol either,..  

Any ideas on how to fix this problem (preferably from the command line) would be much appreciated.

Regards, Pete

---

### Post by caitifty on 2008-12-28
Ok, I finally solved my own problem - it was at the X server end (ie on the machine I was trying to display the Applications on, not on the X Client (the Ubuntu box)  (in X's occasionally confusing nomenclature, the client is where the application runs and the server is where it gets displayed..)

I was attempting to run Amarok (and other apps) on an ubuntu machine and display them over X on a mac laptop.  It'd work fine for ages then suddenly I'd launch Amarok and all the fonts would be so tiny they were unreadable.

I realized today that this was happening consistently after using Grass GIS on the mac (an X11 application).  Quitting Grass, quitting or killing every instance of X11 on the mac, then restarting X11 would suddenly solve the font problem with any application being displayed over X from the ubuntu machine.

I still haven't worked out what the issue is on the mac end, but quitting & restarting X11 is a quick and good enough solution for me..  Hope this helps someone else.

---

