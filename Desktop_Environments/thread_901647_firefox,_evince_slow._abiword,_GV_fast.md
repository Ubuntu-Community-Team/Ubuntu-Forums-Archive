---
title: "firefox, evince: slow. abiword, GV: fast"
date: 2008-08-26
forum: Desktop Environments
---

### Post by margot on 2008-08-26
Some X applications are running very slow while other are as normal. When I look in 'top' I don't see any job taking up a lot of CPU or memory. Firfox, for example, takes forever to come up and then freezes.

I'm running Ubuntu 8.04, GNOME 2.22.3 Kernel 2.6.24-19. Using Xfce.

If I try to change sessions and logon using GNOME or Xmonad, it freezes. Do I need to re-install GNOME ? Any tips on how to diagnose this ?

---

### Post by kerry_s on 2008-08-26
specs please, we need to know what were working with first.

i always find mixing environments leads to problems, i know they say you can have several, but it's really hard to keep things separated.

---

### Post by margot on 2008-08-26
Specs:
Ubuntu 8.04, GONE 2.22.3
Xfce 4 version 4.4.2
Kernel 2.6.24-19-generic #1 SM
Dell Xeon dual CPU 2G Memory

Here's something weird: adding

ifconfig lo 127.0.0.1

to /etc/rc.local

fixed the problem. I have no idea why! I just followed the thread 

[http://ubuntuforums.org/showthread.php?t=188248&highlight=xrdb+ifconfig](http://ubuntuforums.org/showthread.php?t=188248&highlight=xrdb+ifconfig)

on a hunch. I have *no* idea why this worked.

---

### Post by kerry_s on 2008-08-26
hmm, in that case, check your /etc/hosts file and see if its set up right.

127.0.0.1	localhost the.machine name
you just copy the second line to the first line

example mine:

127.0.0.1	localhost debian.myhome.westell.com debian

debian is the host name i picked during setup
westell is my router.

see pic

---

