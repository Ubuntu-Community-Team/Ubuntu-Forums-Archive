---
title: "Filesystem Error"
date: 2006-08-03
forum: Desktop Environments
---

### Post by bart_simpson on 2006-08-03
Hey everybody, I've been using Ubuntu for about a week now after switching from Windows, and everytime I've booted up, I keep getting this filesystem error (note, I wrote this down by hand then typed it, so there may be errors, shouldn't be though):

*checking all filesystems
Ubuntu: Ext3 journal superblock has an unknown read-feature flag set
Ubuntu: Unexpected Inconsistency; Run fsck MANUALLY
(i.e., without -a or -p options)
*File system check failed. Please repair manually 
*CONTROL-D will exit from this shell and continue system starting

I have just been pushing Control-D to force startup, but my system sometimes shutsdown (I should mention that in three consecutive attempts to watch a 10-minute movie on Youtube, 3 times my system has shutdown randomly during the movie) on its own so I thought fixing this could possibly solve the problem. Thanks in advance.

---

### Post by Ramses de Norre on 2006-08-03
Log in a live disc, open up a terminal and run ```
fsck /dev/hda1
``` where you need to replace hda1 with the device node of the actual partition containing errors.
I hope it's not to serious so that all can get fixed..

EDIT: make sure the partition you check isn't mounted!! All data can be corrupted if you run fsck on a mounted partition..

---

### Post by bart_simpson on 2006-08-03
Can I do the terminal commands from the Alternate Install CD instead of the Live CD, because the Live CD for me is really slow?

---

### Post by carlosqueso on 2006-08-03
nope..sadly you'll have to use a live CD....try the xubuntu Desktop cd at: [http://www.xubuntu.com/](http://www.xubuntu.com/) or Morphix lightGUI at [http://www.morphix.org/index.php?option=com_content&task=view&id=26&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=26&Itemid=59) if the ubuntu one is too slow.

---

### Post by bart_simpson on 2006-08-03
Thanks guys for your help, but while I was talking to a friend about the problem, turns out I had this partition (ext3) which I was not able to mount for some reason, so I entered the command:

sudo gedit /etc/fstab

into a terminal and put a # in front of the partition. Now the computer boots up perfectly fine with no errors, thanks for the help.

---

