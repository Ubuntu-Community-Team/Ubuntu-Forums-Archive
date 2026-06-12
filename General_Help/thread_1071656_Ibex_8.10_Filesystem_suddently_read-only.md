---
title: "Ibex 8.10 Filesystem suddently read-only??"
date: 2009-02-16
forum: General Help
---

### Post by ubunny on 2009-02-16
I was copying some files to a backup drive earlier today and no problems.  I go back to it this afternoon, and now all files of the external drive all have a lock on them in nautilus.  Any new attempts to save to the external drive say error "Read Only Filesystem"

ugh

how do I reset the drive that reset itself to read-only back to read-write?  And how can I prevent this in future?

thx

---

### Post by ubunny on 2009-02-16
tried chmod
tried chown
tried chgrp in case you ask

/etc/fstab doesn't report the usb connection so I don't know how Ubuntu is reporting the external drive as read only?

tips would be nice

---

### Post by sarang on 2009-02-16
This is my guess about what happened; I may be completely wrong.

The read-only filesystem developed errors - probably bad sectors, and the problem was exposed / exacerbated by the disk intensive copy operation. Most filesystems are mounted with the [FONT="Courier New"]errors=remount-ro[/FONT] option, which causes the filesystem to be remounted as read-only if errors are detected.

You may reconfigure gnome to remove the [FONT="Courier New"]errors=remount-ro[/FONT] option on drives that it automatically mounts, but I _strongly_ recommend that you do not do that. I hate to say this, but there is a chance that your hard drive might fail in the next few months / weeks / days... if it has important data, I recommend making a backup first and then running a thorough disk-check on the drive. Also, never run a disk check on drives that you expect to be failing before making a backup as the thorough disk check is quite stressful on the drive and ironically might cause it to fail.

---

### Post by ubunny on 2009-02-16
I see.  I don't think the drive is going to fail.  As well there is no entry of the drive in the fstab although it shows under df.  

also, it's only the 3rd partition on the external drive.  all other partitions have been left alone and are not read-only.  I was using some torrents on the 3rd partition, maybe they messed with it?

searching for answers...

---

### Post by bob-linux-user on 2009-02-16
I once found a USB stick that set itself to read only (TBH i can't remember if in Windows or Ubuntu) - I found that it was not fully pushed into the slot. I wouldn't have believed it myself if it hadn't happened to me.This probably isn't your problem at the moment but could be useful in the future.

---

### Post by sarang on 2009-02-16
The [FONT="Courier New"]sudo mount[/FONT] command without any other options will give you info about currently mounted filesystems.

If you want to temporarily make the file system writeable, I suspect that the following will work:

[FONT="Courier New"]sudo umount /media/MOUNT_POINT_OF_EXTERNAL_DRIVE
sudo mkdir ~/tmp-mountpoint
sudo mount /dev/UDEV_ASSIGNED_NAME ~/tmp-mountpoint
[/FONT]

Again, use at your own risk as harm may result if your disk is dying.

---

### Post by ubunny on 2009-02-16
solved it.

unmounted the drive from nautilus by hitting the eject icon
from command line ran sudo mkdir /media/WhateverItIs
then ran sudo mount -t vfat /dev/actualDrive /media/WhateverItIs
and that resolved it.

My guess is that it's not a dire situation as you might be thinking, but more likely a torrent program bailed putting the drive into read-only mode.   Note only one partition was affected.  unmounting the drive and reasserting read-write mode seems to be enough. 
unless I reply back ;)


thanks for the info

---

### Post by sarang on 2009-02-16
Glad to know it works!

I myself wasn't convinced that it was dying, but in such matters it's always good to prepare for the worst :)

---

### Post by bodhi.zazen on 2009-02-16
> **ubunny said:**
> solved it.

unmounted the drive from nautilus by hitting the eject icon
from command line ran sudo mkdir /media/WhateverItIs
then ran sudo mount -t vfat /dev/actualDrive /media/WhateverItIs
and that resolved it.

My guess is that it's not a dire situation as you might be thinking, but more likely a torrent program bailed putting the drive into read-only mode.   Note only one partition was affected.  unmounting the drive and reasserting read-write mode seems to be enough. 
unless I reply back ;)


thanks for the info

glad you solved the problem.

FYI neither fat or ntfs support permissions. permissions are set at the time of mounting the partition and (as you can see) chwon / chmod do not work on fat or ntfs partitions.

To set ownership and permissions use options : uid,gid,dmask,fmask, and umask

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ubunny on 2009-02-16
from your comment though was the understanding that something made it lock, so that helped a lot.

retracing my steps it turns out it's just enough to open the File Browser in nautilus (Application>Accessories>File Browser) then hit the eject icon to unmount the drive, then click on it again for nautilus to remount.  Thus the usermode is not in root but your username.  

also checked the /etc/mstab as this is a list of mounted drives and sure enough all my external partitions are noted there, with rw flags.

cheers

---

### Post by ubunny on 2009-02-16
three files ended up being read-only from the bittorrent program, so I deleted them.  But now I can't delete them from the trash!

I tried going to .local/share/Trash and files but they're not there.

where is the Trash directory from the desktop?

---

### Post by ubunny on 2009-02-16
don't worry about it, i just unmounted the drive again from the File Browser and that allowed me to finally delete the files.  Before it unmounts it has a popup to delete files, and this time it worked.

ok, done.  really.  I hope.

---

