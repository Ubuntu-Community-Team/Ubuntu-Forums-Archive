---
title: "Automounted HDD has wrong name?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by InsaneBeast on 2006-06-04
Hi, I have kind of an odd problem:  An automounted hard-drive is mounted in the right spot in the file-system, but has a nonsense name on the desktop image of the drive.  

I have a fat32 formatted partition I use to transfer data between OS's on a dual boot system (windows & ubuntu).  My fstab reads:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/common   vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


The vfat drive, "common", is mounted in the right spot, but on the desktop, its displayed as "iption file".  The "windows" ntfs partition is mounted and displayed correctly.  I've attached a screenshot to explain:
[[IMG]http://img411.imageshack.us/img411/1414/screenshot1og.th.jpg[/IMG]](http://img411.imageshack.us/my.php?image=screenshot1og.jpg)

Any thoughts on what's going on?  How can I get it to correctly name the drive "common"?   Right-click option "rename" is disabled.  Thanks.

---

### Post by LeSkip on 2006-06-04
I'm suffering from a similar problem, after upgrading from Breezy to Dapper.

The drive mounted under /media/Storage shows up on my desktop as z_)JC%_<t.

What's going on here?

---

### Post by angusvitamin on 2006-06-08
I have the same problem, it happens only to my vfat partition, ntfs is the same as before

---

### Post by scxtt on 2006-06-08
don't know if it matters, but there's a discrepancy b/t your two non-linux entries:

/dev/hda2 /media/common vfat defaults,[COLOR='red']utf8[/COLOR],umask=007,gid=46 0 1
/dev/hda1 /media/windows ntfs defaults,[COLOR='blue']nls=utf8[/COLOR],umask=007,gid=46 0 1

maybe you just need to add "nls=" before the red utf8 and remount it (unmount it first) ...

i pretty much leave it set to "defaults" and add options (if i know what they are / what they do) as necessary ...

---

### Post by InsaneBeast on 2006-06-08
I added the "nls=" to my vfat entry and rebooted to see if it would change the naming, but instead the drive didn't mount at all!  

Mine is a fresh install of dapper, and the added options beyond defaults were put in by the installer.

---

### Post by angusvitamin on 2006-06-08
I found this wiki for renaming automount usb drive. So I did the same thing for for my vfat partition (non-usb) and it worked. Let me know if it works for you guys.

[https://wiki.ubuntu.com/RenameUSBDrive]("https://wiki.ubuntu.com/RenameUSBDrive")

---

### Post by nismoskys on 2006-06-08
weird. my old 40gig ntfs drive used to show up as '0 gb harddrive' on the desktop.

---

### Post by InsaneBeast on 2006-06-12
thanks angusvitamin,  I also found that renaming the partition while in windows somehow carries over to ubuntu.  The partition is now all in caps, but I can deal with that.. I will update everyone if I can figure out how to get names to display in lower and upper cases.

---

### Post by btlee on 2006-06-12
Usually, the drive is named by the lable of the drive.

---

