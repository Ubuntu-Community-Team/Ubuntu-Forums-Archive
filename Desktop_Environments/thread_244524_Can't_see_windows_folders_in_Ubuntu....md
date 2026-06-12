---
title: "Can't see windows folders in Ubuntu..."
date: 2006-08-26
forum: Desktop Environments
---

### Post by guitodd on 2006-08-26
New user warning!!!

I origionally had Suse on this machine with WinXP.  When in Linux I could still get to my Win folders on the same drive or my second drive.   Can't seem to do that with this install.  I go to places/computer and can see the drives.. but when i click.. I get the 'Cannot Mount' error.  

Any ideas?

---

### Post by gruffy-06 on 2006-08-26
You may want to open the following:

System>Administration>Discs on the top panel. Enter your password.

Click the Partitions tab on the correct drive, search for the relevant volume, then click Enable.

---

### Post by guitodd on 2006-08-26
When I click on enable.. nothing happens..  

It does say... 'PATH: None"  Maybe I need to specify a path? Not sure what that should be.

The only enabled volume is my linux partition.

---

### Post by gruffy-06 on 2006-08-26
You may need to make use of the command line at this point.

Use the following to create the directories where your Windows drives will be mounted:

[I]cd /media
sudo mkdir [foldername][/I](repeat for number of Windows drives)

Open Discs from the menu again and in the "Access Path" box, type in /media/[foldername], where *foldername* is the name of the folder you created in the above phase. Click Enable and the drive should be accessible.

The automatic mounting of partitions was previously available in Ubuntu 5.10.

---

### Post by Crooksey on 2006-08-26
are the drives listed in your fstab?

```

gedit /etc/fsatb
```

Post it up.

---

### Post by guitodd on 2006-08-26
This is what it shows...



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by h00s on 2006-08-26
Follow this guide (How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only):
[http://tinyurl.com/sxbnf](http://tinyurl.com/sxbnf)

---

