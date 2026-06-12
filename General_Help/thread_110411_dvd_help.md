---
title: "dvd help"
date: 2005-12-30
forum: General Help
---

### Post by iand675@gmail.com on 2005-12-30
everyone was stumped in the beginners forum, so I'm gonna merge all known information and ask here:
I just did a fresh install on this computer, and so far everything is working fine except for my dvd-drive. It's set up to dual-boot, and it shows up in windows, but in ubuntu, it's nowhere to be found. what can i do to fix this. And before anyone asks, I have tried rebooting to see if it can solve the problem.

I cant even open up the dvd drive by pressing the button on the physical disk, it wont open. It does open when im running windows.
```

ian@ubuntu:~$ sudo eject 
Password: 
eject: tried to use `/dev/hda' as device name but it is no block device 
eject: unable to find or open device for: `cdrom' 
ian@ubuntu:~$

```
here's the output.
but here's the wierd part: the cd rom drive that shows up is actually some strange reference to the partition that ubuntu is installed on. same size, non-ejectable, etc. Why wouldn't this dvd drive show up at all? Do I need to change something in the bios?

---

### Post by darth_vector on 2005-12-30
can you post the output of

ls /media



is there anything in the drive? if there is, try unmounting it:

umount /media/cdromx

and then pressing the eject button on the cd drive.

---

### Post by iand675@gmail.com on 2005-12-30
```

ian@ubuntu:~$ ls /media
cdrom  cdrom0
ian@ubuntu:~$ umount /media/cdrom
umount: /media/cdrom0 is not mounted (according to mtab)
ian@ubuntu:~$

```
and, like i said before: the dvd drive still doesnt open

---

### Post by soulestream on 2005-12-30
might want to post the contents of /etc/fstab also

soule

---

### Post by iand675@gmail.com on 2005-12-30
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
if i didnt know any better, I'd say that it looks like it doesnt exist. any way to manually enter it?

---

### Post by ATAQ on 2005-12-30
Well, reboot the system if all fails and eject the disk before booting, if the drive does not open, well then your drive is wrecked!

---

### Post by iand675@gmail.com on 2005-12-30
still no go. i've tried rebooting, and the drive can open and works in windows, so it is definitely either a bios or ubuntu problem

---

