---
title: "Files becoming corrupt after reboot (NTFS drive using fuse)"
date: 2006-07-12
forum: Desktop Environments
---

### Post by glycerin on 2006-07-12
I have been using the following pages as a guideline to setup my NTFS drive as read/write:

[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs)
[https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)

I can create files/folders inside my mounted NTFS drive (mounted to /media/hda1) without problems. They show up fine in Nautilus and I can use them without problems.

After I restart the computer, however, every file/folder in the drive shows up as unknown. If I click once on any file/folder in Nautilus they all start to dissapear under my cursor. If I reload the folder view they come back but are still unknown. Here's what the command "sudo ls -l" shows:
> glycerin@Hostnamehere:/media/hda1$ sudo ls -l
Password:
total 0
?--------- ? ? ? ?                ? new file
?--------- ? ? ? ?                ? test2.txt
?--------- ? ? ? ?                ? test.txt
?--------- ? ? ? ?                ? Web Downloads


Here's the output of "ls -l /media"
> glycerin@Hostnamehere:/media/hda1$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2006-07-09 05:19 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-07-09 05:19 cdrom0
drwxrwx--- 1 root ntfs 4096 2006-07-10 07:14 hda1


Here's my /etc/fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>		<options>			<dump>  <pass>
proc            /proc           proc		defaults			0       0
/dev/hda1	/media/hda1	ntfs-fuse	auto,gid=1002,umask=0007	0	0
/dev/sda2       /               ext3		defaults,errors=remount-ro	0       1
/dev/sda1       none            swap		sw				0       0
/dev/hdb        /media/cdrom0   		udf,iso9660 user,noauto		0       0


Any help would be appreciated.

---

### Post by BetaguyGZT on 2006-07-12
Read/Write of NTFS filesystems is still a bit dodgy. You've probably seen disclaimers about this.

I recommend that you cease doing any kind of writing to your NTFS partitions, and report what you posted to the Fuse people. Maybe it's something as simple as a setting with the app, or it could be a glitch that needs fixing.

Sorry I couldn't be more helpful.

---

### Post by LKRaider on 2006-07-12
Try booting into windows and chkdsk/scandisk that partition.

I can't think of anything else, as it all seems correctly configured from what you posted.

---

### Post by glycerin on 2006-07-13
Thanks a lot guys. This was my first attempt at support from the Ubuntu community and its nice to see that there are helpful people here to help.

> **LKRaider said:**
> Try booting into windows and chkdsk/scandisk that partition.

I ran chkdsk on the drive and it deleted all of the files which were on the drive (which is fine because they were only test files) and it created a directory which was not there before: "System Volume Information".

Well, that did the trick! The drive now works perfectly with this folder in it. Perhaps it would be a good idea to add to the bottom of the tutorials that if you partition/format the NTFS drive in Linux then the System Volume Information folder is not created and the user must run chkdsk on it in order for it to work correctly.

Thanks again!

---

### Post by LKRaider on 2006-07-13
Glad it worked for you.

I'll add that bit to the tutorial, thanks :)

---

