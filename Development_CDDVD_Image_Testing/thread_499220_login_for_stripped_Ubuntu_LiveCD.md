---
title: "login for stripped Ubuntu LiveCD"
date: 2007-07-12
forum: Development CD/DVD Image Testing
---

### Post by Bartacus on 2007-07-12
Hi everybody,

I could not get an answer at the Dutch fora and I wonder weather you could help me out. I'm making my own live cd from a downloaded live 7.04 Ubuntu desktop CD. I've stripped it down so only a nfs, a ssh and a telnet  daemon start now. I managed to create two partition as ramdisks of 100MB, so my assignement I got is quite finished. Except for one thing: with the stripping I also stripped down the desktop environment, so I start with a prompt.
The thing is that I need a login prompt before I get there to have some kind of security. Can one of you tell me how to get that on a livecd starting in RunLevel 2 with only a textline available?

(I use the reconstructool's chroot to make the live cd)

---

### Post by Bartacus on 2007-07-27
Hi, I still haven't found a sollution myself, but I'll tell what I found out so far. Knowing that Ubuntu doesn't have an /etc/inittab anymore, I searched for what it was they used now -> upstart. According to the stuff I found at the web, I see that I would have to look for /etc/event.d and make the changes there.
When I look there with a chroot, everything seems to be correct: /etc/event.d/tty1
> # tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

When I start the live cd, there is no login prompt _and_ the file mentioned above has changed. It now contains a '/bin/login -f' part instead of the '/sbin/getty' stuff. Does any of you know out of what the live cd takes this information. I have absolutely no clue what so ever and a find statement on 'login -f', 'getty' or 'upstart' didn't bring me any closer.

---

### Post by xanderfiss on 2007-09-10
Hey, I'm doing something similar, so here's what I did to avoid starting X.

sudo cp -rf /etc/rc2.d /etc/rc2.d.back
sudo rm /etc/rc2.d/S13gdm

---

