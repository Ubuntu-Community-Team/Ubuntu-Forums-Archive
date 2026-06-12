---
title: "Trouble with ESD"
date: 2005-09-16
forum: Desktop Environments
---

### Post by jgreath on 2005-09-16
I installed Ubuntu 5.10 preview last night and all went pretty well.  I am extremely impressed with this distribution (my previous experiences having been Gentoo and Slackware 4.x-10.x).  I am, however, having a problem with my sound server that I've never experienced before.

In GNOME, my default audio sink is set to ESD, and the sound server is set to run at start up, but it doesn't.  It did last night, but it's not doing it today.  Strange... must be gremlins :)

Anyway, I can still play audio if I either switch my default audio sink to ALSA or if I execute 'esd &' at a terminal window.

The other oddity is that the sound server is running while I'm looking at the GDM login screen.  It plays a sound when it's ready to accept logins, when I type my password wrong, and even when I log in.  But once I'm logged in, the sound server dies.  I know it's not running as soon as I login as 'ps -a | grep esd' gives me nothing.

Any ideas?

---

### Post by jgreath on 2005-09-16
I just noticed another strange thing.  It seems that my XScreensaver daemon didn't start when I logged in...

---

