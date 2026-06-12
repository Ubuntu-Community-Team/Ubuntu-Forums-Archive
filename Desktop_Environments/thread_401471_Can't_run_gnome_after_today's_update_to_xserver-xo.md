---
title: "Can't run gnome after today's update to xserver-xorg-core"
date: 2007-04-04
forum: Desktop Environments
---

### Post by dean.jones on 2007-04-04
Hi,

I install today's (04/04/2007) update to xserver-xorg-core today (to v. 1:1.1.1-0ubuntu12.1) and gnome no longer starts. I was running the nvidia driver but have since backed-off to nv and that allows gnome to start (but it seems pretty flaky - regular crashes of firefox while writing the message, for example). Anyone else having this problem with the latest update? Any fixes to this update in the offing? 

Best wishes,

Dean.

---

### Post by nuklehed on 2007-04-04
I too ran today's updates and now I get a similar experience. When I first boot up, nautilus loads but never displays a desktop and will automatically restart as if I pressed CTRL+ALT+BACKSPACE. I will be prompted to login again, and when I do I never see the nautilus startup window that usually appears. It just hangs at a blank desktop with no toolbars, icons, or panels. It won't even work in "safe mode." What gives?

---

### Post by justincormier on 2007-04-04
i have the same problem.. i actually think it was due to my idiot decision to not give ubuntu very much disk space.. bout 2.5 gigs.. also i have only been using it for about 13 hours so im just re-installing it now and am only going to lose my mp3 update... 

but now that other people are posting this i feel like maybe there is a bug in the update or something.. im waaaay to new to ever know.

---

### Post by rshawgo on 2007-04-04
I had similar issue, Reinstalled Nvidia Video drivers and all was fine upon GDM restart.
quick view of /var/log/xorg.log indicated that there was an issues setting a display screen at 0:0 so I tried the video driver reinstall and that did the trick.

Ryan

---

### Post by Zer0Nin3r on 2007-04-04
Not really having problems with GNOME starting up, but rather my Beryl server keeps crashing and reverting to the Metacity windows manager.  What gives?

---

### Post by jellyfisharepretty on 2007-04-04
Same here.  I set Beryl to autostart when gnome starts, so now gnome won't start.  It really is beryl that makes the x server restart.  If I go into KDE or XFCE and start beryl manually, I ge thrown back to gdm, just like if I hit crtl+alt+backspace.

All of this has happened after the recent update to xserver-zorg-core.

Anybody know what's going on ?

---

### Post by MontanaMax on 2007-04-04
There are instructions on another thread that worked for me to fix this problem:

> I fixed this without reinstalling the nvidia driver. Try the following first:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

[http://ubuntuforums.org/showthread.php?t=401335](http://ubuntuforums.org/showthread.php?t=401335)

Worked great for me - your mileage may vary...

Good luck!

---

### Post by jellyfisharepretty on 2007-04-04
Hey thanks so much MontanaMax !

That worked, once I restarted X.

Burning down windows now.

---

### Post by Helmi on 2007-04-05
@MontanaMax: also worked for me - great thanks

---

