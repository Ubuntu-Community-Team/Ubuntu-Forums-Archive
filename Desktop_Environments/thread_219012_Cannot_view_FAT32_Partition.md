---
title: "Cannot view FAT32 Partition"
date: 2006-07-19
forum: Desktop Environments
---

### Post by semilemon on 2006-07-19
Hi! I've just taken the plunge to switch to linux! Before installing Ubuntu 6.06, I created a FAT32 partition to use to easily transfer files from my Windows XP install to my Ubuntu install. 

When I go to Places > Computer, I see both Windows' NTFS partition (which I know I can't use) and the FAT32 partition I created. However, when I try to view the contents of either, I get an error message saying "Unable to mount the selected volume."

When I click on "more details", it gives me this:

error: device /dev/hda2 is not removable

error: could not execute pmount

Please help me because I am finally serious about switching, and the first step would be to move my documents onto my linux partition. Thanks in advance!

---

### Post by Paerez on 2006-07-19
can you post your "/etc/fstab" please?
open up the text editor and say open, then double click filesystem, then etc, then fstab, then paste it in here.

---

### Post by semilemon on 2006-07-19
Ok, here is what fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Paerez on 2006-07-19
ok, press ALT+F2 to open the run program dialog. Type in:
```
gksudo gedit /etc/fstab
```
if prompted for your password, enter it.

Now add this line to your fstab:
```
/dev/hda2    /media/fat vfat user,umask=0000,rw    0 0
```
then you will need to run this command:
```
gksudo /etc/init.d/dbus restart
```
then open up "computer" and try to open the fat partition.

---

### Post by semilemon on 2006-07-19
Ok I did as you said. Now when I'm in Computer, I no longer see the four drives associated with my built in card reader. Also, when I try to open the fat partition, I get another error saying "Unable to mount selected volume". When I click show details, it says:

mount: mount point /media/fat does not exist

Also, I tried replacing "hda2" with "hda1" because the FAT32 partition was actually the first partition on the disk.

---

### Post by Paerez on 2006-07-19
ok the replacement was good. I think you will have to restart, but first run this:
```
gksudo mkdir /media/fat
```
then run:
```
gksudo mount -a
```
if that doesn't work, restart, because I don't know the correct command to re-read the drives :(

---

### Post by semilemon on 2006-07-19
Yes, thank-you so much! Restarting fixes everything! I can now read/write my FAT32 Parition! I must say, I really prefer the community aspect of linux to the "let's make tons of money" aspect of windows!

---

### Post by Paerez on 2006-07-19
Cool. You can't write to ntfs partitions (unless you are brave, risky, and handy with a terminal) but you can read from them. You can use the same line for the ntfs, but change it a little:
```
/dev/hda2    /media/ntfs ntfs user,umask=0000,ro    0 0
```
you have to run the mkdir command again to make the ntfs folder. Note that I used hda2 again because I didn't know your real partition name. Also "rw" changed to "ro" (readwrite -> readonly).

happy 'bunting

---

### Post by jimmygoon on 2006-07-19
> **Paerez said:**
> Cool. You can't write to ntfs partitions (unless you are brave, risky, and handy with a terminal) but you can read from them. You can use the same line for the ntfs, but change it a little:
```
/dev/hda2    /media/ntfs ntfs user,umask=0000,ro    0 0
``` you have to run the mkdir command again to make the ntfs folder. Note that I used hda2 again because I didn't know your real partition name. Also "rw" changed to "ro" (readwrite -> readonly).

happy 'bunting

The bit about NTFS partition is really no longer true thanks to ntfs-3g... here's a link for ya: [http://digg.com/linux_unix/Instructions_to_install_NTFS-3G_in_Ubuntu_Dapper](http://digg.com/linux_unix/Instructions_to_install_NTFS-3G_in_Ubuntu_Dapper)
Obviously theres still a risk ;0

---

### Post by Paerez on 2006-07-19
OK, so you still need to be brave, risky, and handy with a terminal, only significantly less so as before.

This is cool and I would check it out, except I dont run windx0r$ any more.

---

