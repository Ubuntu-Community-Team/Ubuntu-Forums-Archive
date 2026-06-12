---
title: "Dell Studio XPS 8000 problems some fixed"
date: 2010-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by munchkinmunchkin on 2010-01-13
I recently got a new Dell Studio XPS 8000 desktop and encountered some problems with the installations of 9.10 karmic.

Spec of PC

i7 860 processor
4gb ram
500gb hard disk
Nvidia GTS240 1mb graphics

1st problem I had that I managed to find a fix for was that the Nvidia screen resolution settings were lost after a reboot. Then after some searching I found that the Nvidia settings must be run as root.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/366360](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/366360)

2nd problem was that the 32bit Flash didn't work properly on 64bit 9.10, so managed to find an easy solution here that works well.

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

3rd problem not resolved, 32bit 9.10 was booting up as far as the white Ubuntu logo screen but no login screen thereafter. Problem is intermittent sometimes login screen appears most times it doesn't Fixed problem only by installing 64bit 9.10

Any more tips, tricks or problem fixes for the same machine would be greatly appreciated.

---

### Post by emaspac on 2010-02-09
same hardware for me:

i7 860 processor
6gb ram
1000gb hard disk
Nvidia GTS240 1mb graphics

and same problem too.
32bit 9.10 was booting up as far as the white Ubuntu logo screen, but _no login screen_ thereafter. if 32bit 9.10 was booted in recovery mode, after the tty-login I can execute 'startx' and it works. 
in my case problem is not intermittent. 100% times login screen doesn't appear.

---

