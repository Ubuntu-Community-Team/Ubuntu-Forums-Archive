---
title: "can't log out of icewm"
date: 2009-02-18
forum: Desktop Environments
---

### Post by rojerd on 2009-02-18
Hi, I just started using xubuntu 8.10 about five days ago, and I did some basic customizing.  I am now using icewm, after using this guide to set it up:
[http://linuxmoderate.wordpress.com/category/dbcos/](http://linuxmoderate.wordpress.com/category/dbcos/)
I am ASTONISHED that when I login it's only using ~76MB of RAM.  I love it.

BUT; for some reason an X terminal of some kind autostarts, and I cannot get rid of it. Because of this, I cannot logout, or shutdown via the GUI (I can sudo shutdown or reboot).

This is a real pain, because otherwise the environment seems awesome.

In a nutshell - xterminal autostarts, can't get rid of it, can't logout.

Any suggestions?  I'd really appreciate any help, I'm a new user and this is a little overwhelming.

Thanks in advance for your time and any advice you can offer
rojerd

---

### Post by Reeman on 2009-02-18
try ctl+alt+bkspace if this returns you to the login then there should be an icon somewhere where you can choose your desktop session. BTW in icewm you access your programs from the terminal just type in the name ie: firefox ...hit return and presto you have your firefox window. You can launch as many terminals as you like and run multiple programs that way. 

Essentially it is a stripped out X based desktop with no menues except for the fact that _**you can launch your program menu with your right mouse button**_ by just right clicking anywhere except over a terminal or launched program.

I use icewm or xfce for critical audio recording work and have all the other desktop crap turned off. I can get at everything I need through a terminal that way and monitor the software as it does things..this way it is much easier to diagnose trouble. Things like wtf happens to my audio device settings if jackd or Ardour crashes.

You can run icewm stripped down and launch any kde or gnome software as long as the libs are in place...just you will not be able to use some of the desktop centered customised utilities for Ubuntu Gnome or Kubuntu.

---

### Post by TenPlus1 on 2009-02-18
IceWM is indeed a great WM and that's the reason I switched to using OpenBox, so that I could shutdown properly...

---

