---
title: "Can not access non-linux HDD Partitions"
date: 2005-09-10
forum: Desktop Environments
---

### Post by xtender on 2005-09-10
Hi, everyone! I' m absolute idiot in Linux. Now I have installed Ubuntu, but when I want to listen music, which is stored on a FAT32 partition I fail to access the partition. I go to Places-Computer-Filesystem-Dev-/dev/hda1
 or /dev/hda2 or /dev/hda3
 etc (I have hda1-hda8) but all I get is "Couldn't display "/dev/hda2"."
I also tried to mount it as it was told somewhere in forum but got "Unable to mount" or "Access denied" - don't remember for sure, but in short, mount failed. How can I access other partitions?

---

### Post by Hairy_Palms on 2005-09-10
u have to mount with the sudo command or u get access denied

sudo mount -t vfat /dev/yourdevice /folder/to/mount/in

should work with hda2 or hda3 as yourdevice

---

### Post by xtender on 2005-09-10
Oh, yea, it worked out! Will that mount at each startup automatcally or am I supposed to do some extra stuff for that?

---

### Post by Christoff UK on 2005-09-10
Ok they wont show on startup to do that....

sudo gedit /etc/fstab

then at the end of the file put this in, adapting it as neccesarry, i.e folder names and device names...

/dev/hda2	/home/chris/Windows	vfat rw,auto,umask=000 0 0

Save then reboot...

---

### Post by Buffalo Soldier on 2005-09-10
How to:[list]
[*] [mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?](http://ubuntuguide.org/#mountunmountntfs)
[*] [mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?](http://ubuntuguide.org/#mountunmountfat)
[*] [ mount Windows partitions (NTFS) on boot-up, and allow all users to read only?](http://ubuntuguide.org/#automountntfs)
[*] [mount Windows partitions (FAT) on boot-up, and allow all users to read/write?](http://ubuntuguide.org/#automountfat)
[/list]

---

### Post by xtender on 2005-09-11
Thanx! Now it' s oK with the partitions!

---

