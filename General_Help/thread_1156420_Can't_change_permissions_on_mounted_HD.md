---
title: "Can't change permissions on mounted HD"
date: 2009-05-11
forum: General Help
---

### Post by Nidding on 2009-05-11
I have my fstap to mount a HD partition on boot. This works fine, but it is owned by root, and is set to not let other users edit or create files. I can't (even when using 'sudo nautilus') change the permissions of the drive. This is pretty annoying as it's my main storage area and I have to open nautilus as root every time I need anything stored. What can I do?

---

### Post by Nidding on 2009-05-11
By the way, my fstab is```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=426ae671-07cd-41c4-a4ae-345d84fda934 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=19275ab6-3634-4d1f-99d0-433cc5fbf3f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#storage
/dev/sda2	/media/Storage	vfat	defaults	0	2
```

I tried to 
```
sudo nautilus
``` and change the ownership of /dev/sda2, but it returned to root after a reboot.

---

### Post by JK3mp on 2009-05-11
can't you just run "su -" root password? If you can't do that i know some people have not set root passwords, (since its not required in ubuntu, it simply nulls out the possibility of logging into root till created.) If you can run that command and become root in terminal you should be able to change permissions the external storage. Though im not sure how it works as far as diffrences between diffrent filesystems (ex. between Windows NTFS and Linux ext3 etc.)

---

### Post by Nidding on 2009-05-11
Ehm. I'm not sure what the su - command is doing?

---

### Post by hobo14 on 2009-05-11
Just add "uid=1000" to the options for that disk (assuming you are the first user in the machine), and/or put in "umask=XXX", where XXX is the permissions mask (ie 000 for full permission, 777 for none)

---

### Post by Nidding on 2009-05-11
> **hobo14 said:**
> Just add "uid=1000" to the options for that disk (assuming you are the first user in the machine), and/or put in "umask=XXX", where XXX is the permissions mask (ie 000 for full permission, 777 for none)

Thanks. It seems to work now :)

---

