---
title: "flash not responding to clicks, can not interact with flash"
date: 2009-01-27
forum: General Help
---

### Post by Hoaxe on 2009-01-27
this is a new bug, flash videos work fine, except click on them has no effect. not even a right click. sound works, video works, it's all good.

If anyone else has had this bug, we should post our package history, submit a bug for the appropriate package, and regress to the previous version until it is fixed.

to post your package download history, open synaptic package manager by going to:
System>Administration>Synaptic Package Manager
from there:
File>History

post all packages from relevant days:

```
Commit Log for Tue Jan 27 01:10:58 2009


Upgraded the following packages:
vim-common (1:7.1.314-3ubuntu3) to 1:7.1.314-3ubuntu3.1
vim-tiny (1:7.1.314-3ubuntu3) to 1:7.1.314-3ubuntu3.1

Commit Log for Mon Jan 26 14:28:12 2009


Upgraded the following packages:
blender (2.46+dfsg-4) to 2.46+dfsg-4ubuntu0.1
xserver-xorg-video-i810 (2:2.4.1-1ubuntu10.1) to 2:2.4.1-1ubuntu10.3
xserver-xorg-video-intel (2:2.4.1-1ubuntu10.1) to 2:2.4.1-1ubuntu10.3
zsnes (1.510-2.1ubuntu1) to 1.510-2.1ubuntu1.1

Commit Log for Wed Jan 21 14:44:11 2009


Upgraded the following packages:
cheese (2.24.1-0ubuntu1) to 2.24.2-0ubuntu0+intrepid1
libpoppler-glib3 (0.8.7-1) to 0.8.7-1ubuntu0.1
libpoppler3 (0.8.7-1) to 0.8.7-1ubuntu0.1
libv4l-0 (0.5.6-1~intrepid1) to 0.5.7-1~intrepid1
libv4l-dev (0.5.6-1~intrepid1) to 0.5.7-1~intrepid1
poppler-utils (0.8.7-1) to 0.8.7-1ubuntu0.1
xserver-xorg-video-i810 (2:2.4.1-1ubuntu10) to 2:2.4.1-1ubuntu10.1
xserver-xorg-video-intel (2:2.4.1-1ubuntu10) to 2:2.4.1-1ubuntu10.1

Commit Log for Tue Jan 20 04:24:47 2009


Installed the following packages:
libmotif3 (2.2.3-2)
menu (2.1.40ubuntu1)
motif-clients (2.2.3-2)
```

i just hope this is just me or somehow fixes itself just like it broke it's self because i really don't see any flash packages that got updated... worries me... :(

---

### Post by Hoaxe on 2009-01-27
oh man, i can't believe i'm the only one with this problem.

i can't even go through flash splash pages...

---

### Post by TheLions on 2009-01-27
i had same problem (on x64 Ubuntu), fixed it with installation of x64 Flash from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

just extract it to /home/username/.mozilla/plugins/

---

### Post by Hoaxe on 2009-01-27
> **TheLions said:**
> i had same problem (on x64 Ubuntu), fixed it with installation of x64 Flash from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

just extract it to /home/username/.mozilla/plugins/

well, it seeeems like a reboot fixed my problem. this is still a bug though. just because i update a package doesn't mean it should stop functionality of any specific type of app or process on my computer.

r.d.

---

### Post by erlguta on 2010-02-06
i Have the same problem.
You and me and a looot of people more. Look at the bug, how many people are affected:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

### Post by euloiix on 2012-01-05
For me, TheLions' solution worked. I was also running on linux x64 bits (10.04 Lucid if that matters). 

Thank you very much

---

