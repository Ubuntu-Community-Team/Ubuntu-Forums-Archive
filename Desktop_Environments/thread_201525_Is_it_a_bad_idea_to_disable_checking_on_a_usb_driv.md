---
title: "Is it a bad idea to disable checking on a usb drive at bootup?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by michaeljb2005 on 2006-06-21
Hi I was having trouble with linux correctly identifying/checking my usb drive at bootup so I disabled the check in fstab by setting the value to 0.  Is this a bad idea?  Or does it not really matter since it is a removable drive?  I mount the drive at /home so does that make a difference in whether it should check it or not?  Also just to mention it the part that is mounted to /home is only a partition of the whole usb device.

---

### Post by mssever on 2006-06-22
It would definitely be a good idea to check the partitions on your USB drive, as doing so can identify and or fix many filesystem problems before they become serious. I don't think that it makes any difference whether the disk is USB, IDE, SCSI, or whatever. However, if you're having problems with the check on bootup, you might consider running e2fsck (assuming it's an ext2/3 partition--otherwise use the appropriate utility for your filesystem type) as a cron job--perhaps weekly.

---

### Post by michaeljb2005 on 2006-06-22
[QUOTE=mssever]It would definitely be a good idea to check the partitions on your USB drive, as doing so can identify and or fix many filesystem problems before they become serious. I don't think that it makes any difference whether the disk is USB, IDE, SCSI, or whatever. However, if you're having problems with the check on bootup, you might consider running e2fsck (assuming it's an ext2/3 partition--otherwise use the appropriate utility for your filesystem type) as a cron job--perhaps weekly.[/QUOTE]

[QUOTE=rai4shu2]Very simple: MS Office and Internet Explorer (which are not generally available on Linux distros). Microsoft has used this unfair trade practice to not only reduce the value of Linux, but also Apple or any other competitor.[/QUOTE]

When I run e2fsck I get this

mike@mike-laptop:~$ sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Never mind I ran it on sdb5 which is the particular partition and it said it was clean.  Still don't understand why it's having a problem at bootup.

---

### Post by mssever on 2006-06-22
Try dropping the -b option. When I wes testing just now, I had no problems with ```
sudo e2fsck /dev/hdb6
``` but I got the same error with ```
sudo e2fsck -b 8193 /dev/hdb6
``` 
Of course, I might have set my block size wrong, but e2fsck should be able to figure it out if you allow it to work the default way.

One other complication I discovered as I was testing in preparation for this reply: The partition needs to be unmounted before running e2fsck. Running umount /home might not work if the system is up and you're logged in. You could take the computer down to single-user mode to do the check
```
sudo telinit 1
do stuff
telinit 5
``` 
I haven't thought of a way to check your disk automatically, though, if you can't reliable unmount /home from cron.

By the way, you quoted a post about Windows. Do you use the partition in question from Windows? If so, then e2fsck won't work because ext2/3 filesystems don't work at all in Windows, which means that your filesystem is probably fat32 or NTFS. Type ```
fsck<tab><tab>
``` for a list of the various commands for your filesystem.

---

### Post by michaeljb2005 on 2006-06-22
[QUOTE=mssever]Try dropping the -b option. When I wes testing just now, I had no problems with ```
sudo e2fsck /dev/hdb6
``` but I got the same error with ```
sudo e2fsck -b 8193 /dev/hdb6
``` 
Of course, I might have set my block size wrong, but e2fsck should be able to figure it out if you allow it to work the default way.

One other complication I discovered as I was testing in preparation for this reply: The partition needs to be unmounted before running e2fsck. Running umount /home might not work if the system is up and you're logged in. You could take the computer down to single-user mode to do the check
```
sudo telinit 1
do stuff
telinit 5
``` 
I haven't thought of a way to check your disk automatically, though, if you can't reliable unmount /home from cron.

By the way, you quoted a post about Windows. Do you use the partition in question from Windows? If so, then e2fsck won't work because ext2/3 filesystems don't work at all in Windows, which means that your filesystem is probably fat32 or NTFS. Type ```
fsck<tab><tab>
``` for a list of the various commands for your filesystem.[/QUOTE]

I umounted and ran e2fsck on sdb5 and it was found clean.  That was the partition in question.  I guess i'll see if there's a problem on the next boot.

Yep still had a problem on the next boot.  It gives me a similar error message as the one I quoted before when trying to read sdb.

---

### Post by michaeljb2005 on 2006-06-22
I'm just going to leave checking disabled for that partition.  All it does when I manually check it is confirm that it's fine.  I'm not sure what the problem is, but it always seems to mount fine anyway.  Thanks for the help.

---

### Post by mssever on 2006-06-22
That's probably a good idea given the impracticality of checking it on a regular basis. It would be a good idea, however, to manually check it any time it isn't cleanly unmounted (after a power outage, for example). That's when problems are the most likely to crop up.

---

### Post by michaeljb2005 on 2006-06-22
[QUOTE=mssever]That's probably a good idea given the impracticality of checking it on a regular basis. It would be a good idea, however, to manually check it any time it isn't cleanly unmounted (after a power outage, for example). That's when problems are the most likely to crop up.[/QUOTE]

Just so you guys know what I mean when I say "check" is that I set <pass> in fstab to 0 instead of 1 or 2 and so on.  Is that what you understood that I meant?

---

### Post by mssever on 2006-06-22
Yes. All that is is periodic filesystem checking.

---

