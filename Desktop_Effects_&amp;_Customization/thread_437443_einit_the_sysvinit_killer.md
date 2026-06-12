---
title: "einit: the sysvinit killer"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by rmh3093 on 2007-05-08
I just wanted to let all of you Ubuntu users that there is a new init system out now called eINIT. It is written in C and is configured via a few easy to edit XML files. eINIT is extremely customizable. My entire system (including mounting disks, bringing up network interfaces, alsa, hal, dbus, cups, ntpd, cpufreq,... etc.) is all up in a matter seconds from the time the kernel is finished doing thing. The information about the init system can be found at:

[www.einit.org](www.einit.org)
or
#einit @ irc.freenode.net

Ubuntu is the next linux distro slated to be supported... not that you cant build eINIT now... there are just no packages specifically for Ubuntu. I encourage everyone to stop in the IRC channel.

The source can be download and built like so:

svn checkout svn://svn.berlios.de/einit/trunk/einit
cd einit
./configure --enable-linux --use-posix-regex
make install

---

### Post by PlancksCnst on 2008-04-06
I just heard about einit and have been looking for info about einit on Ubuntu.  I read on their compatability page that "the modules need adjustments".  What does this mean?  I'm trying to figure out if I'll be in over my head and screw up my system if I try it.

---

### Post by reacocard on 2008-04-06
Um, we already have a replacement for sysvinit, it's called upstart and has been in Ubuntu since edgy. It currently run mostly in sysv-compatibility mode right now, but I expect that they'll start migrating more scripts to in ubuntus after hardy. It's already possible to move ones entire startup to upstart, and in fact [jdong has already done this]("http://ubuntuforums.org/showthread.php?t=727224"), it just needs to get implemented in Ubuntu itself.

---

