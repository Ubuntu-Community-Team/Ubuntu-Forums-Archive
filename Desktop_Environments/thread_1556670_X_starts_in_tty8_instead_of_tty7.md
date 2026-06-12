---
title: "X starts in tty8 instead of tty7"
date: 2010-08-19
forum: Desktop Environments
---

### Post by rtimai on 2010-08-19
I don't know when this started but I noticed today that my desktop is starting in tty8 instead of the normal tty7. tty7 shows a blinking text cursor in the upper-right corner which doesn't respond to the keyboard.

I don't guess this is serious, but I'm REALLY curious! I have installed Ubuntu Tweak, but I can't see anywhere where I may have made any changes to cause this.

In a search for answers, what mention I could find about sessions suggest editing (with gksudo) either /etc/inittab or /etc/event.d, but these files appear no longer to be located in /etc in Lucid (or Gnome 2.30.2 , but elsewhere. So I don't want to attempt any changes. Can someone provide more current information? 

Ubuntu 10.04 Lucid
Kernel 2.6.32-24-generic
Gnome 2.30.2
Session Gnome

ADDED: I restarted and the desktop is back in tty7. I think this may have something to do with my recent experimenting with running OpenBox in place of Metacity. Anyway, if anyone knows how the number of available sessions is set, I'm still interested. Thanks!

ADDED 09/01/2010: Restarting causes X to start in the standard tty7 but, logging off then back on consistently reproduces the "X in wrong tty" problem (if it is a problem.) This is why I thought this was related to testing an alternate window manager (OpenBox.) Actually it is connected to the logon/off process when switching wms. I am running Metacity (compositing turned off) and without Compiz, if this helps.

A web search for "tty8" yields various inconclusive discussions about a running process that prevents tty7 from being deallocated when logging off, which makes it unavailable when logging back in.

[http://osdir.com/ml/debian-user-debi...ads.html#00662](http://osdir.com/ml/debian-user-debi...ads.html#00662)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=348033](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=348033)
[http://comments.gmane.org/gmane.linu...an.user/374025](http://comments.gmane.org/gmane.linu...an.user/374025)

If anyone is aware of potential undesirable consequences with having the X desktop running in other than tty7, please let me know. The workaround for my case (one user logging on/off,) is to select Restart at the login prompt instead of logging back on to Gnome desktop after testing an alt window manager.

---

### Post by Insperatus on 2010-09-06
Also using

Ubuntu 10.04
kernel 2.6.32-24-generic
GNOME 2.30.2

I've noticed the same phenomenon of X running in tty8 after several times logging in/out.  Curious also as to the cause :)

---

### Post by asmoore82 on 2010-09-06
I think it has something to do with modern distros' "Switch User" ability.

---

