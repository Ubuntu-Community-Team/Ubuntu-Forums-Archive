---
title: "Ubuntu can't see into Linspire and vice versa"
date: 2005-12-17
forum: General Help
---

### Post by silverfire on 2005-12-17
Hi, all. New Ubuntu user here and I have a question for you. I have Linspire on one hard drive (hda) and Ubuntu on my other (hdb). Linspire is using Reiserfs and Ubuntu is using the default (I think ext3?). I had Mandrake/Mandriva and a Windows partition on hdb previously, and Linspire was able to see into both those OSes just fine. 

Unfortunately, it can't now.

Likewise, I can't see into the Linspire install from Ubuntu. I go to /mnt and there's nothing. 

I tried checking /etc/filesystem, as a friend recommended, but I don't seem to have that in either OS. Is this a sign of a faulty install, or is this handled in some other way in Ubuntu?

Any help you can offer will be greatly appreciated, as I would like to be able to get to my data from either OS, instead of having to reboot and log into Linspire just to get a password from my password program. ;)

---

### Post by kairu0 on 2005-12-17
The correct file is /etc/fstab.

Check if your linspire partition is specified in that file:

```
sudo gedit /etc/fstab
```

---

### Post by silverfire on 2005-12-17
Thanks. Just checked it and found that it doesn't even mention hda at all. How would I go about resolving this?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```

---

### Post by kairu0 on 2005-12-17
Add a line like this to the end of that file:

```

/dev/hdaX     /mnt/mountpoint     reiserfs     defaults      0     2

```

Change X to the correct number of your Linspire partition.

---

### Post by aysiu on 2005-12-17
First, you have to create a mount point for Linspire: ```
sudo mkdir /linspire
``` Then, add in a line about it in the /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Add in this line: ```
/dev/hda1  /linspire  reiserfs  defaults  0  0
``` Save. Then ```
sudo mount -a
sudo chown -R silverfire:silverfire /linspire
``` This assumes, of course, that Linspire is on /dev/hda1 and that your username is silverfire.

---

### Post by silverfire on 2005-12-17
Thank you. That worked.

---

