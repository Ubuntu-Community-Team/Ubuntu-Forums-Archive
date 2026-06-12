---
title: "Where did my hard drives go???"
date: 2010-10-26
forum: Desktop Environments
---

### Post by LughGlas on 2010-10-26
So I have Zorin (yeah yeah, but its Ubuntu based) installed on one of my hard drives.  On the other 250GB drive I have, I still have XP.  When I log into XP, I have two of my hard drives, and am missing one.  When I log in to Zorin (which means I have to change the boot order in my BIOS), I only see one of the hard drives.  Each drive is partitioned.  All I want to do is to get rid of XP and have Zorin acknowledge all of my hard drives.  How do I do this?!

---

### Post by 3Miro on 2010-10-26
This is a bit confusing, so let me see if I get this right. You have two hard drivers, one with Zorin and one with windows XP. Windows XP sees both harddrives (I suppose from Administrative tools), however, XP will not be able to use the Zorin harddrive unless you install special software. On the other hand, Zorin only "sees" its own harddrive. Is this correct?

I am having hard time with the Zorin's web-page, I don't seem to get which environment they are basing it on. From the screenshots it looks a lot like LXDE, however, this would be an odd choice for a "new to Linux" oriented system. On other pictures the file manager looks like Thunar, which is the XFCE manager ... This one of the hard parts of Linux, you can never tell by the looks. If you are using Nautilus (the default for Ubuntu) file manager, you should be able to see the extra partitions on the left of the window and you should be able to click on them.

Here is the distribution independent way to figure it out. Go to the terminal/console (or konsole) and type
```
 sudo fdisk -l 
```
This should list stuff like:

```
 
..................
Some Unimportant stuff .....
.....................

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         996     8000338+  82  Linux swap / Solaris
/dev/sda2   *         997        4731    30001387+  83  Linux
/dev/sda3            4732       30401   206194275   83  Linux

..................
Other Unimportant stuff .....
.....................

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2611    20972826   83  Linux
/dev/sdb2            2612       20887   146801970   83  Linux
/dev/sdb3           20888       38913   144793845    7  HPFS/NTFS
 
```
I have two harddrives with three partitions each. All but one partition are formated for Linux (one if the swap).

While at it, you can check to see which one of these commands will work:
```
nautilus
```
```
thunar
```
```
pcmanfm
```
this will tell use where to go from here.

---

