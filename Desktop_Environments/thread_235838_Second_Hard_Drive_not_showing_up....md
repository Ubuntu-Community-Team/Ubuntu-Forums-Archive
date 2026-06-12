---
title: "Second Hard Drive not showing up..."
date: 2006-08-13
forum: Desktop Environments
---

### Post by raintheory on 2006-08-13
Hello all, I have been browsing other peoples threads that have had a similar problem but have not found a solution to my issue as of yet./..

  Wondering if anyone has any suggestions.,  Basically I've installed a 2nd hard drive, created a mount point, etc. etc....   But my 2nd drive doesn't show up.

  fdisk -l

```
[FONT="Fixedsys"]Disk /dev/hda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2398    19261903+  83  Linux
/dev/hda2            2399        2491      747022+   5  Extended
/dev/hda5            2399        2491      746991   82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2494    20033023+  83  Linux
[/FONT]
```
  
   etc/fstab

```

[FONT="Fixedsys"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/media/Storage	ext3	defaults	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]
```

Anyone have any ideas as to why this isn't showing up for me?

Thanks in advance!

EDIT:  I'm not sure why the fstab looks all garbled in here, but it doesn't look that way in gedit...

---

### Post by maniacmusician on 2006-08-13
is the hard drive you're trying to set up the /dev/hdb1 entry in your fstab?

Which desktop environment are you using? (Ubuntu, Kubuntu, Xubuntu, etc)

by your beans count i'm just assuming you're a newbie, so sorry if this seems elementary.  Have you actually made the folder /media/Storage? as in like "sudo mkdir /media/Storage"? if so what are the permissions and ownership of this folder

---

### Post by raintheory on 2006-08-13
> **maniacmusician said:**
> is the hard drive you're trying to set up the /dev/hdb1 entry in your fstab?

Which desktop environment are you using? (Ubuntu, Kubuntu, Xubuntu, etc)

by your beans count i'm just assuming you're a newbie, so sorry if this seems elementary.  Have you actually made the folder /media/Storage? as in like "sudo mkdir /media/Storage"? if so what are the permissions and ownership of this folder

using Ubuntu Dapper.  The second drive is /dev/hdb1...

These are the steps I took after formatting the drive as ext3:

- created directory using $ sudo mkdir /media/Storage

- made directory writable $ chmod 777 /media/Storage

then i edited /etc/fstab and tried mounting the drive $ sudo mount -a

the drive wasn't showing so I rebooted just in case...  but it's still not there.

Thanks for your help, yes I am fairly new to ubuntu by the way, only been using it for a few months now.

---

### Post by vijirajan on 2006-08-13
Can you paste the output of the mount command?

```

sudo mount

```

---

### Post by raintheory on 2006-08-13
Well, oddly enough it's showing up now...   All I did was reboot two more times, but it's there.  (couple questions below though).   

Weird.

Anyway, 

sudo mount

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hdb1 on /media/Storage type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

A couple questions though...   Should I have put the mount point in /mnt instead of /media or doesn't that matter?  Also, is there anything I should have entered in fstab under "options" besides defaults? 


I'll be sure to post back if anything funny happens from this point on.

Thank you so much for your time, wish my drive luck!  ;)

---

### Post by vijirajan on 2006-08-13
Glad to know the drive shows up now :) It doesn't matter where you mount the partition as long as that directory exists with the proper permissions. For the "options" default should be fine.

---

### Post by cantormath on 2006-08-13
tutorial on adding drive
[http://personal.riverusers.com/~thegrendel/lnxpg3.html](http://personal.riverusers.com/~thegrendel/lnxpg3.html)
another tutorial on adding drive
[http://yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)

Hope it helps...

---

