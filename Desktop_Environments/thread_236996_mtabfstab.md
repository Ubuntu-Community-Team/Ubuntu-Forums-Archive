---
title: "mtab/fstab"
date: 2006-08-15
forum: Desktop Environments
---

### Post by jimmymac on 2006-08-15
Alright guys,

What is the differences between mtab and fstab?  
Does there need to be a line in both for the machine to recognise a partition?

TIA

Jimmy

---

### Post by jimmymac on 2006-08-15
OK so the reason I was asking this is that when I try to unmount a drive I get:

james@jameslaptop:/media$ sudo umount -a
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

My /etc/fstab is this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3	/vmware	vfat	defaults	0	0
/dev/sda1     /media/new     ntfs-3g     silent,umask=0,locale=en_GB.utf8,no_def_opts,allow_other    0    0

And yes I'm trying to get ntfs-3g to work.  (I like to tinker, it's usually the best way to learn)

and /etc/mtab is:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/hda3 /vmware vfat rw 0 0
/dev/sda1 /media/New\040Volume ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

Any ideas?

MTIA

Jimmy

---

### Post by fluffnik on 2006-08-15
Briefly, fstab is a configuration file which tells mount what to do and mtab is a generated file written by mount to show what it understands the current state of play to be.

Not sure why your trying to do a "umount -a", that unmounts **all** the contents of mtab and is only really apropriate during shutdown.

I suspect "umount /dev/sda1" (or "umount /media/new" which is the same thing) is what you want.

---

### Post by givré on 2006-08-15
/etc/fstab is the file use to set partition.
/etc/mtab is a file containing the information about all device/partition actually mounted, you shouldn't not edit.
Your problem, i guess is you create a /etc/mtab~ by editing it or whatever, so you should delete it:
```
sudo rm /etc/mtab~
```
it should work after that

---

### Post by jimmymac on 2006-08-15
Hi guys,

Thanks for the replies.
There is no mtab~ but there is a fstab~, I presume this is created after editing it to add the ntfs-3g part:

/dev/sda1     /media/new     ntfs-3g     silent,umask=0,locale=en_GB.utf8,no_def_opts,allow_other    0    0

Anyhoo,

If no longer get that error message that I stated earlier.
If I have the ntfs-3g line in fstab I can't mount the ext volume.  I just get an error saying:

Couldn't mount device '/dev/sda1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

The only way to get my drive back up (read only of course) is to remove that line from fstab, then disconnect the drive and reconnect.

Any other ideas?

MTIA

Jimmy

---

### Post by jimmymac on 2006-08-15
Alright guys,

Just so that you know, I actually read some more of the HowTo: ntfs-3g.
I'm going to see if a mate of mine has still got a windows partition that I can chkdsk the ext. drive on.
This might also solve the problems I was having with resizing my NTFS partition in GParted!

Thanks for all your help, I'm really beginning to love Ubuntu and this forum!  I'm never made to feel stupid by the people on here even though I've asked some real dumb questions!  How to make a Linux n00b feel welcome!

Cheers!

Jimmy

---

### Post by fluffnik on 2006-08-16
> **jimmymac said:**
> Alright guys,
Thanks for all your help, I'm really beginning to love Ubuntu and this forum!  I'm never made to feel stupid by the people on here even though I've asked some real dumb questions!  How to make a Linux n00b feel welcome!

No dumb questions that I've noticed.

I've been all *nix since 1998 so I'm hoping to learn something from your mission to have safe read-write access to your ntfs partitions - I don't have any to play with. :mrgreen:

We're all sharing a great adventure in a world where you *can* find out what's going on and share what you've learned so that the next traveller can learn a little more and share it with you.

---

### Post by jimmymac on 2006-08-17
Cheers for that,

OK so I got to a mate's computer and ran chkdsk /f on my ext hdd.

Then went back to my machine and tried to mount the drive and got the same error message:

Couldn't mount the device /dev/sda1: Operation not supported Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
mount Failed.

Any other ideas?

MTIA

Jimmy

---

