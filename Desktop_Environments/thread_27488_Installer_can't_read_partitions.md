---
title: "Installer can't read partitions"
date: 2005-04-16
forum: Desktop Environments
---

### Post by wumpus on 2005-04-16
I am trying to change a mandrake/windows dual boot to a Hoary Kubuntu (or ubuntu) dual boot.  I get as far as the partition editor where it refuses to read my partitions.  If I boot the DVD live, fdisk can read the partitions.  Other notes:

Mandrake uses lilo, but since lilo shows up as an option, this doesn't seem to be a problem.

The entire disk seems to be an extended (windows) partition.  I don't remember doing that and am surprised it still boots.

I've had this problem with other systems (mainly red hat (same intstaller) and SUSE.  I think it has something to do with Mandrake.

I'd prefer to keep my windows (98) partitions, since I expect to have to install windows over kubuntu, and then muck around with grub (note I've been using lilo all this time).  Is there a good way to convince kubuntu live to install on the partitions it sees?

Wumpus

---

### Post by polemicz on 2005-04-16
what kind of hd do you have? there are installer problems with ez-drives (can't pass the parameter hdx=remap). the 2.4 kernels automatically did the remap, not the 2.6.

---

### Post by KDE-fan on 2005-04-17
I had the exact same problem when I switched from Mandrake to Kubuntu. I solved it by recreating  my first partitions with Mandrake-10.RC1-Mini installation CD. That enabled the Kubuntu installer to read all my partitions perfectly.

---

