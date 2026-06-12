---
title: "cannot locate libaudio.so.2??"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Anything Generic on 2006-06-15
Skype won't run because it says I'm missing libaudio.so.2, but when I apt-get libaudio2, it says it's already installed.  I'm new, and confused.  Help!

eric@ubuntu:/$ /opt/skype/skype
/opt/skype/skype: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory


eric@ubuntu:/$ sudo apt-get install libaudio2 libaudiofile0 lib32asound2
Reading package lists... Done
Building dependency tree... Done
libaudio2 is already the newest version.
libaudiofile0 is already the newest version.
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by Anything Generic on 2006-06-15
Solution:

Go to Synaptic and get the ia32 for Openoffice.  The dependencies were in there (strange!)

---

