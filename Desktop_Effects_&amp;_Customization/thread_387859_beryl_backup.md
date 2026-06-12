---
title: "beryl backup"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by evilc on 2007-03-18
I have finally got beryl the way I want now what I would like to do is backup my configuration in case of a disaster happening. Could someone tell me what to backup or do I just backup my home folder, also ( bit of an off shoot)if I backup my home folder and reinstall with a newer version of Ubuntu would all the additional programs I have installed show up with when replacing the home folder with the backup.

tia,

---

### Post by AtrejuT on 2007-03-19
Hi evilc,

I'm afraid making a backup of your home folder will only save the settings, but not the actual programs.
What you should do is make
a) a backup of your homefolder using e.g. rsync, or, if it is on a separate partition from the rest, partimage.
b) boot a live CD, this can be ubuntu but very useful is also the system rescue cd found here:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) 
and make a backup of the partition on which / is residing. If you do not use a separate partition for /home just this last part will be good enough.

This will allow you to completely restore your system to the current state  - having a backup is always a good idea, independent of beryl.

atreju

---

