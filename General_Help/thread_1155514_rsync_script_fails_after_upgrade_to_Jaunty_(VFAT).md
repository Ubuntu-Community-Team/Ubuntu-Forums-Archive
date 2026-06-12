---
title: "rsync script fails after upgrade to Jaunty (VFAT)"
date: 2009-05-10
forum: General Help
---

### Post by bricedebrignaisplage on 2009-05-10
I want to backup some data to an external harddrive (EXT2 to VFAT)

Here is what I was doing under Hardy:

mount the external harddrive with appropriate options to handle case in names on VFAT (found this solution in some online tutorial):
mount /dev/sdb1 /mnt -t vfat -o shortname=mixed,iocharset=utf8,umask=0000,gid=100,uid=1000

the rsync command: (can't remember what modify-window is for)
rsync --modify-window=1 -rtv --delete /media/bigdisk/Documents /mnt

It used to work fine. But after I upgraded to Jaunty it wants to retransfer the whole thing. I did a dry run only so I don't know if it would retransfer it again and again.

what can be the reason? And what can I do?

---

### Post by atrocity on 2009-05-10
> **bricedebrignaisplage said:**
> 
the rsync command: (can't remember what modify-window is for)
rsync --modify-window=1 -rtv --delete /media/bigdisk/Documents /mnt


modify-window is the allowable timestamp difference in seconds...in your case, if the files are a second apart, they're considered the same and should not be retransferred.  (Hopefully I'm explaining that correctly.)

> **bricedebrignaisplage said:**
> 
It used to work fine. But after I upgraded to Jaunty it wants to retransfer the whole thing. I did a dry run only so I don't know if it would retransfer it again and again.

what can be the reason? And what can I do?

I don't know why it's happening or what you can do, but I'm having the same problem.  In my case, it's well over a terabyte of data that I need to keep synced up, so basically I can no longer do backups until this is resolved.  Not good.

I tried increasing the modify-window to 60, but it still wants to copy everything.

My stuff is pretty convoluted...I run it all from a Perl script.  Some stuff is copied from the internal EXT3 drive but the bulk of it is going between external FireWire and USB drives.  One of backups goes from an external USB drive on a Windows machine to an external USB drive on the Ubuntu machine.  Crazy as it is, it all worked before.

---

### Post by atrocity on 2009-05-10
> **atrocity said:**
> 
My stuff is pretty convoluted...I run it all from a Perl script.  Some stuff is copied from the internal EXT3 drive but the bulk of it is going between external FireWire and USB drives.  One of backups goes from an external USB drive on a Windows machine to an external USB drive on the Ubuntu machine.  Crazy as it is, it all worked before.

A couple other things:

1. My drives are all mounted via fstab.

2. I wasn't smart enough to do a dry run at first...I actually started it and left the house, not realizing what it was doing until I got back several hours later.  I killed it and tried a dry run, at which point it didn't want to copy the files it had already copied.

Has something changed in regard to file timestamps?

---

### Post by l33tminion on 2009-11-06
I'm having the same problem.  The disk in question mounts as vfat... as far as I remember, it mounted as ntfs previously, but I could be remembering wrong.

---

### Post by l33tminion on 2009-11-06
Rather, I should say I'm having the same problem after an upgrade to Karmic...

---

