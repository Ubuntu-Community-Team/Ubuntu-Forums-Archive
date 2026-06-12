---
title: "[SOLVED] Completely Remove Ubuntu 8.10"
date: 2008-12-09
forum: General Help
---

### Post by TopEnder on 2008-12-09
Good Day and Thanks in advance,  Currently running aTriple Boot - Windows XP Home, Hardy Heron 8.04 and Intrepid Ibex 8.10 (my experiment) system. I have had a look at Intrepid Ibex8.10 and would prefer to go back to Dual Boot System with Windows XP Home & Hardy Heron 8.04 for it's LTS.  Have no idea how to go about it so I am asking the Forum's Experts.  All OS are on different HDs.  Hardy Heron 8.04 - /boot/grub/menu.lst is intact.  I not sure what information need to post on the formum, no doubt someone will tell me what they need to see about my system to help me achieve my aim.  Thanks, TopEnder

---

### Post by louieb on 2008-12-09
1st set the PC up so that when it boots - it uses the Hardy installs version of GRUB.  My guess is its booting to the Intrepid version of GRUB. The steps are the same as if you had installed XP after installing Ubuntu. So this should work for you. [Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Once that is done you can use the space occupied by Intrepid for whatever you need or want. 

Good stuff on GRUB: [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

IF you have more questions please post the output of ```
sudo fdisk -l
``` (lowercase L) this will list your partition table

---

### Post by TopEnder on 2008-12-09
Thanks for the reply I will try it later today & advise.
```
sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc308c308

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS [COLOR="Magenta"]** Windows XP Home **[/COLOR]
/dev/sda2            5223        9964    38090115    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000933ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9731    78164226   83  Linux   [COLOR="Magenta"]** Ubuntu Hardy Heron 8.04 **[/COLOR]
/dev/sdb2            9732        9980     2000092+  82  Linux swap / Solaris
/dev/sdb3            9981       19457    76124002+  83  Linux

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6767f78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2490    20000893+  83  Linux   [COLOR="Magenta"]** Ubuntu Intrepid Ibex 8.10 **[/COLOR]
/dev/sdc2            2491        9762    58412340    b  W95 FAT32
/dev/sdc3            9763       10011     2000092+   5  Extended
/dev/sdc5            9763       10011     2000061   82  Linux swap / Solaris

```

---

