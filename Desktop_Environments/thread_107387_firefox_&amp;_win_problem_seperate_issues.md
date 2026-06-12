---
title: "firefox &amp; win problem seperate issues"
date: 2005-12-22
forum: Desktop Environments
---

### Post by ESPOiG on 2005-12-22
i know how to get my windows partition mountd but i dont know how to get it mountd automatically at everystartup

sudo mkdir /media/Windows
sudo mount /dev/hda1 /media/Windows/ -t ntfs -o umask=0222

what can i do to get it mountd at boot or when i login

and also my firefox is f*kd i click it, it says loadin application firefox or sumtin and then just doesnt load WTF? so wat to i do to fix this aswell

---

### Post by towsonu2003 on 2005-12-22
For windows partitions: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29%7C%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29%7C%28windows%29)

For firefox, take a look at this [http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile) and give it a try with a **new profile**. Also, try loading it from the terminal (command is firefox) to see whether you get any error messages.

---

### Post by ESPOiG on 2005-12-22
THX ALOT... ill see wat happens

---

### Post by ESPOiG on 2005-12-23
i got lost in the auto mount windows partition thingy it said it wasnt there or availible in the terminal... isnt there just sumtin i type in terminal to fix it

---

### Post by towsonu2003 on 2005-12-23
hmmm... okay here is my fstab (see below): ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /fat32          vfat    defaults        0       0
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /ntfsboot       ntfs    defaults        0       0
/dev/hda2       /ntfsdocs       ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This was for reference only...



Now try doing the following and hopefully it will be fixed:
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```
and in the last line, add this: 
```
/dev/hda1       /Media/Windows       ntfs    defaults        0       0
```
then save and exit. finally make sure you are not using the windows driver **at all** and: ```
sudo umount -a
sudo mount -a
```
umount -a will unmount everything it can (not dangerous) and mount -a will mount everything it reads from this fstab file. 

Good luck.

If it doesn't work again (even after reboot), please post output of ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by ESPOiG on 2005-12-23
thx man it workd and now im very happy :D.... THX

---

### Post by towsonu2003 on 2005-12-23
you're most welcome ;) enjoy :)

---

