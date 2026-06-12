---
title: "Gnome freezing after upgrade to 9.04"
date: 2009-10-11
forum: Desktop Environments
---

### Post by oskar.m on 2009-10-11
hi

after upgrading from 8.10 to 9.04 I have troubles with my desktop environment Gnome. here what I can tell so far:

after logging on Gnome runs stable. Just when I open any(!) application after a couple of seconds the system becomes irresponsive. Meaning: mouse moving slow, can not change to another terminal (ctrl + Fn), can not kill X via ctrl+alt+backspace.

this happens any time since I upgradded to 9.04

dmesg does not show anything suspicious neither does Xorg.log. I currenlty have no clue how to troubleshoot. any ideas about log files to look; into are welcome.

BTW same behavior if I run XFCE instead of Gnome so it seems to be a general X server thing.

cheers

---

### Post by wojox on 2009-10-11
What kind of graphics card?

---

### Post by oskar.m on 2009-10-12
Graphic card: Radeon 9600 
 
Since the upgrade to 8.10 I am using the (opensource) ati driver instead of the fglrx driver.

---

### Post by oskar.m on 2009-10-12
well problem solved. I checked the Ubuntu bug tracker for infos on Radeon 9600 and found [this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/406045"). Finally configuring my xorg.conf manually solved the problem.

The added entry was 

```
Device
...
Option "AGPMode" "1"
...
End Device
```Things seem to be working stable now.

---

