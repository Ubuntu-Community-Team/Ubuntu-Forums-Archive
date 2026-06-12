---
title: "[SOLVED] Modify / Delete read-only files"
date: 2009-01-03
forum: General Help
---

### Post by zami on 2009-01-03
I just pulled a lot of files from a little MMC disk onto my desktop hard drive, and I'd like to delete the files on the MMC disk now.  When I hit delete, I get the message about them being immediately deleted instead of moved to the trash (no problem here), then

> 
Error while deleting.
There was an error deleting [dir name]
Error removing the file: Read-only file system


Any help?

The permissions on the disk (and sub directories etc) are Owner: create and delete files.  Everything else is "none" or "--".

I tried chmod'ing the directories in the disk via the command line with no luck (but I'm a slob with the command line so that may well be my fault.)

I tried gorilla chmod'ing with 
gksudo nautilus, browsing to the disk, and changing the permissions from the permissions tab under properties... still no luck.  When I do that I get 
> 
The permissions could not be changed.
Sorry, could not change the permissions of "disk": Error setting permissions: Read-only file system


The contents of the disc are mostly linux generated files I've stored there, .pdf, .jpg, .doc,  along with a lot of camera generated .jpgs that have been viewed in both Windows and Linux systems.  

I haven't had this problem with my camera disks before so I'm pretty baffled here.  
Any help would be much appreciated.

-zami

---

### Post by BoardStupid on 2009-01-03
This might be a daft question, but is there a read-only switch on the card? I know I've forgotten about them in the past and been completley baffled as to why I couldn't do anything with the card.

---

### Post by lswb on 2009-01-03
2 things come to mind. First, I'm not sure about MMC but SD cards have a little movable tab to mark them as read only. (Though it does not actually make the card unwriteable; it depends on the host system to detect the position and act appropriately)

More likely it has a fat or dos filesystem and is being being mounted read only. You could try 
```

sudo mount -o remount -o rw /media/disk

```
substituting the actual mountpoint of the MMC card for /media/disk.

I'm not sure offhand, you may also be able to do this from the gui by right-clicking on the disk icon or from nautilus somewhere.

---

### Post by zami on 2009-01-06
```
sudo mount -o remount -o rw /media/disk
```

worked perfectly, thank you!

And the little lock/unlock slider on the physical disk was agood idea actually, and one I'd looked over.  This *is* an SD card, not and MMC - both fit in my camera and I just grabbed the closest to me to see what they were called - my fault!  That wasn't the issue, but I'd certainly hate if it had been and no one had pointed out the obvious to me, so thanks to you both for the lock suggestion, too.

:)

-zami

---

