---
title: "Formatting accidentally stopped at 75%"
date: 2008-12-14
forum: General Help
---

### Post by krahenke on 2008-12-14
I recently got a laptop with Ubuntu on it, and when I was trying to install Windows on VMWare, I accidentally chose to format my MP4 player instead my partition that I made before that. The formatting stopped at 75%, now I can`t format my player anymore, neither can I load anything from it. At the hard disk data of the play it says that it has 0 mb.

Is there any way to fix my mistake?

Cheers,
KraHen

---

### Post by sedawk on 2008-12-14
When you plug in your player it should be mapped to some scsi device
like /dev/sdX where X is a, or b, or c, or ...
Let's asssume it is /dev/sdf. The partition(s) on that player are
then mapped to /dev/sdf1, /dev/sdf2, etc.
(you can see this when running "dmesg" on command line after inserting
 the player and waiting a few seconds).

From command line run (example)
sudo fdisk -l /dev/sdf

You should see some partitions, the sizes and file system types.
If some of the data is broken you can use fdisk interactively
to fix it. You can also use command line tools to format the
partition (again) if the size of the partition looks okay.
Command line tool for formatting a partition with a dos
file system is "mkfs.msdos".
(Some of the above might only work if you unmount the old
 partition first. This can be done via the menu entry "Places").

(If there was something important on the stick you can try
 first to use a "carving" tool to rescue the data. I'm not
 sure if "carving" tools works for MP3 files).

If you are unsure how to continue post the output of sudo fdisk -l here.

---

### Post by blazemore on 2008-12-14
run sudo gparted from the liveCD.
Choose the correct device from the drop down menu on the right.
I take no responsibility for you choosing the wrong device and deleting stuff.

Delete any partitions on the device.
Create a new one, and format it with the required filesystem (Fat32 etc).

---

### Post by geirha on 2008-12-14
Try [testdisk](apt://testdisk). It may be able to recover the previous partition.

---

### Post by krahenke on 2008-12-14
I can`t see my player in fdisk -l. It only drops out my two main partitions (although it drops out my D: partition 2 times o.o)

---

### Post by sedawk on 2008-12-14
Start your computer without the player and open a terminal
to get a command line.
Run "dmesg -c" to clear the message buffer.
Now plug in the player. Wait a few seconds.
Run "dmesg" and post the output here.

---

