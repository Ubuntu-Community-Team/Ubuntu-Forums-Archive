---
title: "Flash USB memory unmounted! How to restore?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by richardstrausbourg on 2006-02-25
Somehow my flash memory unmounted. Maybe I clicked it off? Somehow? Help??

It reads "Mount Error" and then
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

Before, when I put in the flash drive in the front USB port, it would be instantly recognized. Now...nothing.
Any ideas?


How can I remount this USB drive?

---

### Post by pestilence4hr on 2006-02-26
Perhaps try

```
sudo rmmod scsi_mod
sudo rmmod usb_storage
sudo modprobe scsi_mod
sudo modprobe usb_storage
```

Then see what 

```
ls -ltr /dev/sd*
```

shows.  Try mounting one of those, e.g.

```
mkdir mymountpoint
sudo mount /dev/sd(letter/number from above) mymountpoint
```

---

### Post by richardstrausbourg on 2006-03-30
Thanks for the help! Working ok.

---

### Post by tebibyte on 2006-04-10
admin@edubuntu:~$ sudo rmmod scsi_mod
ERROR: Module scsi_mod does not exist in /proc/modules

I need more help. My floppy drive doesn't work either.

---

### Post by Ramses de Norre on 2006-04-10
Does sudo modprobe scsi_mod work? Maybe the module wasn't loaded.
What does your /etc/fstab look like? Is there a line for your floppy?

---

### Post by tebibyte on 2006-04-11
I got the first step of post 2 done. I tryed to mount it and got the following error
```

admin@edubuntu:~$ ls -ltr /dev/sd*
brw-r-----  1 root plugdev 8, 0 2006-04-11 09:22 /dev/sda
brw-r-----  1 root plugdev 8, 1 2006-04-11 09:22 /dev/sda1
admin@edubuntu:~$ mkdir mymountpoint
admin@edubuntu:~$ sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
admin@edubuntu:~$ sudo mount /dev/sda1
Password:
admin@edubuntu:~$
admin@edubuntu:~$ sudo mount /dev/sda1
Password:
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
admin@edubuntu:~$

```
The fstab is as follows:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
mtab is as follows:
```

/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
/dev/hda1 /media/hda1 vfat rw 0 0
/dev/hda2 /media/hda2 ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0

```
My flopply can't be mounted
the error says:
Unable to mount the selected volume.
mount: I could not determine the filesystem type, and none was specified

The floppy works fine in other computers.I believe that the two errors are related.

I am sort of new when it comes to linux and especialy the command propt. Any more help whould be greatly appreciated. Thank you for your help so far

---

### Post by pestilence4hr on 2006-04-11
[QUOTE=tebibyte]
```

admin@edubuntu:~$ mkdir mymountpoint
admin@edubuntu:~$ sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab

```
[/QUOTE]

You forgot to specify the mount point.  You need to try e.g.

```
admin@edubuntu:~$ sudo mount /dev/sda mymountpoint

```

---

### Post by tebibyte on 2006-04-12
```
max@edubuntu:~$ sudo modprobe scsi_mod
max@edubuntu:~$ sudo modprobe usbstorage
FATAL: Module usbstorage not found.
max@edubuntu:~$ sudo modprobe usb_storage
max@edubuntu:~$ sudo rmmod usb_storage
max@edubuntu:~$ sudo rmmod scsi_mod
ERROR: Module scsi_mod is in use by sd_mod
max@edubuntu:~$ sudo rmmod sd_mod
max@edubuntu:~$ sudo rmmod scsi_mod
max@edubuntu:~$ sudo modprobe scsi_mod
max@edubuntu:~$ sudo modprobe usb storage
FATAL: Module usb not found.
max@edubuntu:~$ sudo modprobe usb_storage
max@edubuntu:~$ ls -ltr /dev/sd*
brw-r-----  1 root plugdev 8, 1 2006-04-12 07:59 /dev/sda1

/dev/sda:
total 0
max@edubuntu:~$ mkdir /dev/sda1
[COLOR="Red"]mkdir: `/dev/sda1' exists but is not a directory[/COLOR]
max@edubuntu:~$

```
Ok... that is wierd. It exists but is not a directory. What does that mean, and what can I do to fix it? Thank you for your help so far pestilence4hr. I appreciate it very much. :)

---

### Post by pestilence4hr on 2006-04-12
Right.  You might want to go back and retry my original instructions, you were doing quite well until you left off the last part of the last command.  

You shouldn't be issuing the last command you have pasted here (mkdir /dev/sda1).

---

### Post by tebibyte on 2006-04-13
[QUOTE=pestilence4hr]Right.  You might want to go back and retry my original instructions, you were doing quite well until you left off the last part of the last command.  

You shouldn't be issuing the last command you have pasted here (mkdir /dev/sda1).[/QUOTE]

I got it to work and can access it from meda/sda1!

Uh...do I have to type that in each time I plug the USB? How can I get it to auto mount?

In addition I have to be root to unmount the floppy. When I put in a new floppy disk the floppy page doesn't refresh to show the files on the new floppy, even when I press refresh.
Thanks for being paient with me

---

### Post by Aimsleey on 2007-11-13
I am having the same same problem and am getting this error-

root@Fheoir:/home/amy# sudo mount /dev/sda1 mymountpoint
mount: you must specify the filesystem type

Any help greatly appreciated!!!

---

