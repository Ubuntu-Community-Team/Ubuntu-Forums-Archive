---
title: "Keeps booting into 1024x768 resolution"
date: 2011-11-21
forum: Desktop Environments
---

### Post by bradpower2011 on 2011-11-21
Hi :)

I was having some trouble with an app, and after some browsing through the forums found out that a possible solution would be to use a 2.6 kernel. Well, I tried that and it didn't work out. I've removed that older kernel and though everything would be OK. However, now my 11.10 installation boots into a 1024x768 resolution every time I turn on my laptop. That can easily be fixed by going into Display Settings, but it'll be back at that 4:3 resolution next time I restart. I found out that editing xorg.conf should fix it, but that file is no where to be found in /etc/X11 in my Oneric installation.

Any help here?

---

### Post by jimmydean886-2 on 2011-11-21
Try the /usr/share/x11/xorg.conf.d directory and see if there's anything in there.

--jimmydean886-2--

---

### Post by bradpower2011 on 2011-11-21
Thanks!
There are various files there, but no xorg.conf. 

The files there are:

10-evdev.conf
10-evdev-quirks.conf
10-evdev-trackpoint.conf
50-synaptics.conf
50-vmmouse.conf
50-wacom.conf
51-synaptics-quirks.conf

If it matters, there is an "X" shortcut on /etc/X11 that leads to a file called "Xorg" but I can't edit that one as it just crashes the text editor.

---

### Post by bradpower2011 on 2011-11-22
*Bump*

Nobody knows? How about this: is there a script or something I can make run at startup to automatically change the resolution?

---

### Post by bradpower2011 on 2011-11-22
Well, this was solved.

It seems that Jupiter changed the screen resolution after I installed the older kernel. After changing the screen resolution setting in Jupiter, the problem is no more! :)

---

