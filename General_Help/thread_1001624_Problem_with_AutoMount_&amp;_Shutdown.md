---
title: "Problem with AutoMount &amp; Shutdown"
date: 2008-12-04
forum: General Help
---

### Post by codename_nixon on 2008-12-04
Hi
   Iam using ubuntu 8.10 and im facing few problems  

1. I have 2 SATA hdd's 320 gb and 500Gb both have 2 partitions each,
i have ubuntu installed on the HDD 1 i.e 320Gb[it is set as primary HDD in the bios] over a 50gb ext3 partition.

i installed ntfs 3g after doing some search to automount but it only auto mounts 1 partitons i.e a 50Gb ntfs partiton on HDD2 500Gb 

**hers the ss of ntfs config tool**

[http://www.imagebay.com/bay.php?view=10818_Screenshot-ntfs-config.png](http://www.imagebay.com/bay.php?view=10818_Screenshot-ntfs-config.png)

**[B]heres the output of fstab**

[http://bayimg.com/baMDJaAbE](http://bayimg.com/baMDJaAbE)

[B]the partitons are shown in places but and i mount them by clicking on them
heres a SS[/B]
[http://bayimg.com/BAMdkaAbe](http://bayimg.com/BAMdkaAbe)

**hers the fdisk-l** SS

[http://www.imagebay.com/bay.php?view=10817_Screenshot-2.png](http://www.imagebay.com/bay.php?view=10817_Screenshot-2.png)

how to automount them???


2. when shutdown or reboot ubuntu gets stuck on a blinking cursor screen

what to do guys??

---

### Post by Yuki_Nagato on 2008-12-04
I noticed the Big Red Arrow at the top right of your desktop.  Have you installed all of the updates recently?

This page has some good information on auto-mounting.  Apparently, the first solution to try will be an automatic script.  But that could be sketchy.  Other solutions involve manual editing of the fstab.

_[https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29)_

Here is more specific information on fstab:

_[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)_

---

### Post by Yuki_Nagato on 2008-12-06
When GRUB first pops up and gives you a choice of options, try selecting and options that is something similar to "failsafe."

---

