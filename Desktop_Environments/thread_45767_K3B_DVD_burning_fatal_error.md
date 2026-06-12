---
title: "K3B DVD burning fatal error"
date: 2005-07-01
forum: Desktop Environments
---

### Post by cotcot on 2005-07-01
Gnomebaker does not work for DVD burning. Gnomebaker returns "umount: /media/cdrom0 is niet aangekoppeld (volgens mtab)"  when trying to format a DVD-RW.
Translation : "umount : /media/cdrom0 is not mounted (according to mtab)

I copied 2 lines with mount cdrom0 and cdrom1 from fstab to mtab. Then I get the message that root login is required.

Is there any tip or suggestion ? 
 Thanks

---

### Post by Xian on 2005-07-01
Is it correct to say that Gnome can auto-mount a DVD in a desktop session, but using this same drive Gnomebaker complains it is not mounted?

---

### Post by cotcot on 2005-07-02
Yes Xian that i it.

This is my fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1      /media/windows	vfat	umask=000	0	0

and this is my mtab :

/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda1 /media/windows vfat rw,umask=000 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by cotcot on 2005-07-04
I stop trying Gnomebaker to work because I got k3b working fine. I had a fatal error on k3b but this is solved (the DVD-RW disk that I used was OK).

---

### Post by DarkManX4lf on 2005-07-06
this is weird, gnomebaker said the same thing for me that my cddrive isnt mounted??? and then i massively clicked something and then it starts burning !

weird

---

