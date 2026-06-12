---
title: "can't mount windows NTFS drive"
date: 2006-08-16
forum: Desktop Environments
---

### Post by striketh on 2006-08-16
I'm trying to mount my windows drive and get the error (shows trying to unmount first so you know it's not mounted..as far as the OS knows):
umount: /dev/hda1: not mounted
$ sudo mount /dev/hda1 /media/windows
mount: /dev/hda1 already mounted or /media/windows busy

I remember when I installed ubuntu I selected an option for it to mount the drive. I've tried to get into the folder but even running as root ist still won't let me in. I tried setting it to mount in the fstab but it seems like it's not going to work since it's already mounted somewhere on the system.

This is my entire fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/media/windows	ntfs	nls=utf8,umask=0222	0	0

Can anyone help me figure out how to unmount it from whereever ubuntu has it mounted at so I can gain access to the drive? 

Thanks.

---

### Post by Reb on 2006-08-16
What is the output of 'mount' when you have this problem?

---

### Post by striketh on 2006-08-16
$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)

---

### Post by striketh on 2006-08-16
I removed the entry from the fstab, ran sudo mount -a and got this:

$ sudo mount /dev/hda1
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

Adding it back in and doing the following yields this result:

$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy

$ sudo fuser -c /dev/hda
$ sudo fuser -c /dev/hda1
$ sudo fuser /media/windows

Nautilus properties also show no owner/group and read only permissions. I'm pretty lost as to what direction to go at the moment.

Any ideas?

---

### Post by striketh on 2006-08-16
I figured it out..tried it on the 2.6.15 kernel and it works fine. So..it seems to be a kernel issue. Now to try another compile and hope I can fix it. Any recommendations?

---

### Post by striketh on 2006-08-16
I just re-compiled the 2.6.17 kernel (making sure NTFS file system support was checked) and I get this:

$ sudo modprobe ntfs
FATAL: Module ntfs not found.

Can anyone help me get NTFS support fixed now that I narrowed it down?

---

### Post by dillbertdabomb on 2006-08-16
I have the same problem : I went to system > admin. > disks and went to my drive it said "active" and than I clicked browse after that and when I clicked my hard it says "you do not have the permissions to access this drive", well its nice to know im not the only one with the problem...

and you say it does this after install? than how did you make the windows partition smaller?

---

### Post by striketh on 2006-08-16
Hmm? I didn't make the drive smaller. I installed fuse and set it up according to the ubuntu dapper guide and that got me in business. My windows drive is mounted and working just dandy now thanks to fuse.

---

### Post by Herman on 2006-08-16
>  and you say it does this after install? than how did you make the windows partition smaller?
Hello, dillbertdabomb, I use a GParted LiveCD when I want to resize my partitions.
 **Managing My Partitions with GParted**..............................................................................[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#Managing_My_Partitions_with_GParted")
   
> I have the same problem : I went to system > admin. > disks and went to my drive it said "active" and than I clicked browse after that and when I clicked my hard it says "you do not have the permissions to access this drive", well its nice to know im not the only one with the problem... Here is my web-page about how to mount other filesystems in Ubuntu. I have explained things as clearly and in as much detail as I know how. If there is anything you are still uncertian about, please don't hesitate to contact me, and I'll fix the web-page so it will be easier for others in the future. [COLOR=#000000]                 Mount Other Filesystems.......................................................[/COLOR][Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")

We can read from an NTFS drive but not write any data to it. If we want s drive to share the data and write to it from both operating systems we make a FAT32 data partition.
All the best, dillbertdabomb, Regards, Herman :D

---

