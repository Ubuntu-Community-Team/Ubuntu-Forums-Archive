---
title: "Gnome Problem With Dual Head Separate X screens"
date: 2009-04-23
forum: Desktop Environments
---

### Post by carcara on 2009-04-23
I'm running Ubuntu 8.10 with a nvidia card dual-head setup("Separate X screen"), the "Absolute" display is my monitor and my TV is "RightOf". It works fine.
The only problem is, on my TV, when I click on Panel>Places>... only the "Computer" will open on the TV (the display I'm working at), everything else will open on my monitor.

It's not a big problem since after opening "Computer" I can browse the filesystems and when I click on any media file it will play on the TV, just fine.
The big anoyance started when I decided to install Ubuntu 9.04 on a spare disk(dual boot) on the same box and configure it the the same way as the 8.10 installation.

On 9.04, everything I click on(on my TV) will open on my monitor.
If, for instance, I force Nautilus to open on my TV (display :0.1) and from that file browser window I try to open a media file(actually, any kind of file) it will always open on my monitor (:0.0).
I have tried all kinds of changes on my xorg.conf and nothing changes. 

I even copied the whole directory trees /etc/X11/, /etc/gdm and /usr/share/gdm/ from the 8.10 installation over the 9.04 and nothing changes.
On the same box I also have a Fedora 10 installation and it behaves exactly the same as the Ubuntu 8.10.

At work I have the same setup (nvidia dual-head Separate X) on Fedora 8 and it works perfectly, everything I click on will open on the display I'm working at.
I use the same xorg.conf file on all the installations.

I installed IceWm on Ubuntu 9.04 and started the X servers on both displays and it works like a charm, everything opens on the correct display.  
Now I'm pretty sure the problem is some how related to Gnome but I can't figure out exactly what and how to fix it.

Thanks in advance.

---

