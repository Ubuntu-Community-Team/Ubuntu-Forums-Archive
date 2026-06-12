---
title: "How to run X/ubuntu with IceWM?"
date: 2008-03-24
forum: Desktop Environments
---

### Post by ccesarjj on 2008-03-24
I'm trying to make my Ubuntu system as light as possible and I don't really want to change to a another GNU/Linux distro right now. (My hardware: Desktop pentium III with 256MB RAM, 10Gb HD) I've changed my desktop from GNOME to XFce to speed up the system, and there was an improvement but not a dramatic one. In another PC with much less resources (pentium III 32 MB RAM) I installed delilinux with Icewm and It worked fine and really fast (however, I had some trouble to make certain programs work properly). Do you know if there's a way in which I can manage to run my X/ubuntu system with a light window manager such as IceWM in my 256MB Machine (or even in the 32MB RAM one)? How can I do it? Is there any serious advantage on using a complete desktop such as GNOME or XFCE rather than just a window manager if I only do some technical wordprocessing (Doc and LaTeX documents), simple spreadsheet calculations, handle some small databases and play a music CD every once in a while ? Thanks!

---

### Post by ugm6hr on 2008-03-24
*icewm* and *menu* are available from Synaptic.

Just install them and reboot.  You can chose the WM from "Session" in GDM (login window).

---

### Post by Jareth on 2008-04-10
Hi, I found this and have tried it out today.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Was looking for some pointers myself when I found your thread. It involves getting the Ubuntu minimal cd and when you choose the windows manager its Icewm.

I have an old pc with a similar spec actually and its running it alot better than Gnome, although gnome wasn't unbearable. I just fancied a change as well.

It really is a minimal install though. I'm just looking now for some way to mount my USB hard drive to read from it. :confused: Its good to know the terminal as well!

---

### Post by kerry_s on 2008-04-10
debian is much more better on the old stuff, it's smaller, faster, more stable. also once you get your perfect setup your good to go, no keeping up with releases.
net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

just uncheck everything at the package selection stage for a base install.
log in as root
apt-get install xorg (your wm)(what ever else)
exit
log in as user
startx

my systems 450mhz 256mb ram, i run etch/lenny

---

