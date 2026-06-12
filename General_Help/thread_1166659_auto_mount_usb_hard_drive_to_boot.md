---
title: "auto mount usb hard drive to boot"
date: 2009-05-22
forum: General Help
---

### Post by Bigpat on 2009-05-22
:frown: Hello everyone I've just registered to this forums and this is my first post. I installed ubuntu 9 on my western digital external hard drive with success. However, when I boot I get the grub menu then the ubuntu splash screen and then a black screen with a list of errors. After doing some research I learned that my external drive is not mounting for it to boot, I would have to unplug the usb drive plug it back in and then type the word exit and then the the drive starts to boot. I also learned it might have something to do with my fstab. If there is something wrong here please feel free to correct me. I would very much appreciate it if someone can help me. the constant pluging and unpluging is annoying.

Here is my fstab.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=20501925-769a-47d6-afea-fe724e7e2995 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7db6c564-ad58-4008-9e5b-ca69c4ff0497 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

