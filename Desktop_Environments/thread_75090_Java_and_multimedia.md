---
title: "Java and multimedia"
date: 2005-10-13
forum: Desktop Environments
---

### Post by lean on 2005-10-13
Hello,
I was wondering if somebody would set up a repository with java and multimedia.
Backports are no good, since they also upgrade other packages.
I just want a ubuntu stable, where I easily can get properitary things. Easy-ubuntu is even worse, since it tries to change a lot of packages - firefox etc.

Anyone up for the task?

---

### Post by KingBahamut on 2005-10-13
Would be difficult to do so. 

What exactly are you trying to accomplish? You want to install the JRE and thats it? Just hte multimedia packages and thats it?

---

### Post by raaguileraa on 2005-10-13
lean:
I've been using Hoary for a while and found this:

on synaptic, add these repository

"deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted"
"deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java"

the packages you could find usefull are:
gstreamer0.8-mad
gstreamer0.8-faad
gstreamer0.8-faac
libdvdcss2
gstreamer0.8-ffmpeg
sun-j2sdk1.5

Good luck!
-----------------------------
from [http://weblog.topopardo.com/archives/000243.html](http://weblog.topopardo.com/archives/000243.html) (spanish)

---

### Post by drogoh on 2005-10-13
[QUOTE=raaguileraa]lean:
I've been using Hoary for a while and found this:

on synaptic, add these repository

"deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted"
"deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java"

the packages you could find usefull are:
gstreamer0.8-mad
gstreamer0.8-faad
gstreamer0.8-faac
libdvdcss2
gstreamer0.8-ffmpeg
sun-j2sdk1.5

Good luck!
-----------------------------
from [http://weblog.topopardo.com/archives/000243.html](http://weblog.topopardo.com/archives/000243.html) (spanish)[/QUOTE]


That is outdated.  Look at the stickies here: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by raaguileraa on 2005-10-13
Thanks for the tip drogoh!

---

