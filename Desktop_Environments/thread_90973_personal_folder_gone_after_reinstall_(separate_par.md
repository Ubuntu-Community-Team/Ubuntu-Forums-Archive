---
title: "personal folder gone after reinstall (separate partitions)"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Alex99 on 2005-11-16
Hi,

Can anyone explain this? I did a reinstall twice, and after the second time, the personal folder was gone. Having the computer search for the missing files doesn't give any results.

I reinstalled Ubuntu 5.1 on my root-partition, while I didn't touch the home-partition. After the first reinstall, the personal folder was to be found under /media/hda5 (name of home-partition), while under /home/massmann (my name) there was a new personal folder. 

So far, so good, but after the second reinstall (again no changes to the home-partition), the files I had edited in /home/massmann after the first reinstall were gone! /media/hda5 shows only what was there after the first reinstall.

Where could I find the missing data? Thanks,

Alex

---

### Post by Lambert on 2005-11-16
When you reinstalled the first time, it sounds like you mounted the /home partition in a new place and your old home folders were mounted in /media/hda5. On the first reinstall, did you install the os on a single partition or did you partition out and install / on one and home on another?

If you reinstalled the whole os on the same partition the same way on the second reinstall then the /home tree from the 1st reinstall will be gone.

run fdisk -l and post output.

---

### Post by wrtrdood on 2005-11-16
User files are placed in /home.  If this has not been defined by mounting a partition at /home then the mount point is all you will see plus whatever users have been added.  In the partitioning tool you must rename the mount point from the default of /media/hda5 to /home.  This is done by highlighting the selection and pressing enter.  You'll be shown a list of default names.  Select home and hit enter again.  During install, an entry will be created in /etc/fstab that mounts the /dev/hda5 partition on /home rather than the default on /media/hda5.  As a result, you will then see the expected results under /home.  As mentioned, the installation process will automatically create the /home directory.  If it is not used as a mount point for another partition it becomes the directory itself.

---

### Post by Alex99 on 2005-11-17
**Lambert**:
This is my fdisk-l-output: (it's in German - but I guess those are standard values that you'll figure out)

> Platte /dev/hda: 80.0 GByte, 80026361856 Byte
255 K&#246;pfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 &#215; 512 = 8225280 Bytes

Ger&#228;t  boot.     [COLOR="Red"]Anfang[/COLOR]        Ende     [COLOR="Red"]Bl&#246;cke[/COLOR]   Id [COLOR="Red"] System[/COLOR]
/dev/hda2            [COLOR="Red"]1035[/COLOR]        4742    [COLOR="Red"]29784510[/COLOR]    5  [COLOR="Red"]Erweiterte[/COLOR]
/dev/hda4              [COLOR="Red"] 1[/COLOR]        1034    [COLOR="Red"] 8305573+ [/COLOR] 83  [COLOR="Red"]Linux[/COLOR]
/dev/hda5            [COLOR="Red"]1035[/COLOR]        4681   [COLOR="Red"] 29294496[/COLOR]   83 [COLOR="Red"] Linux[/COLOR]
/dev/hda6           [COLOR="Red"] 4682 [/COLOR]       4742     [COLOR="Red"] 489951[/COLOR]   82  [COLOR="Red"]Linux Swap / Solaris[/COLOR]

**wrtrdood**:
I didn't quite get it. Part of the problem is that I have a personal folder both in /media/hda5 and /home/massmann, and those personal folders are different ones.
I tried the partitioning tool GParted, which shows me two two to four partitions:

> hda4   ext3              8.111 MB  (that's where the system is installed)
hda2   extendended   29.086 MB
   [INDENT] hda5    ext3               28.608
    hda6    linux-swap       478[/INDENT]

There's a small down-pointing arrow to the left of "hda2" and the following two lines are indented, which apparently means that hda5 and hda6 are subdivisions of hda2.

However, the list doesn't show /media/hda5, and on selecting a section and pressing enter I'm only shown the information on that part, but I can't change anything.

---

