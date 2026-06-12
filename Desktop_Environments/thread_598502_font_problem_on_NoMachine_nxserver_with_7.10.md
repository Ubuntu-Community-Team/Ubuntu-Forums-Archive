---
title: "font problem on NoMachine nxserver with 7.10"
date: 2007-10-31
forum: Desktop Environments
---

### Post by corkypa on 2007-10-31
I just did a fresh install of 7.10 server i386, then did an install of gnome-core to get a desktop environment. I then installed the NX server free edition from nomachine's site (version 3.0.0-74). On my Windows client, I upgrade to the latest version (3.0.0-83). When I try to connect, everything goes ok until the screen with the large "M" appears. That winks out almost immediately. Looking in syslog, I see

 ERROR: Error when monitoring session: Could not open default font 'fixed' 
NXSessionMonitor::__setSessionStatus'

Based on [this thread]("http://ubuntuforums.org/showthread.php?t=291290"), I tried installing the font server, and even made sure I had "127.0.0.1       localhost unix" in /etc/hosts, but that didn't change anything.

NoMachine says the server is supposed to work in 7.10, so the problem may be related to my starting with the server version instead of the desktop version when I did my installation.

Anybody else solve this problem?

---

