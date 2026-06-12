---
title: "automounting USB disk as ext2: permissions problems"
date: 2007-11-19
forum: Desktop Environments
---

### Post by CeeEss on 2007-11-19
Ubuntu 7.10 2.6.20-15-generic #2 SMP

I've read a lot of threads related to automounting vfat and NTFS filesystems but my issue is with ext2/3 filesystems.

Automounting ext2 USB disks poses no problem, but the perms on the mountpoint (/media/usbdisk, usbdisk-1, etc) are *almost always* 700 with owner root.  I've seen one or two rare cases where ownership is given to the current user but haven't been able to track down why.  Of course, copying to the root-owned disk sans-sudo results in denial, so all copies to the disk have be done using sudo.

When a normal user attempts to eject the disk, an error dialogue pops up to the effect that the user is not permitted to Eject, then the drive ejects with a dirty filesystem - not nice.

In gconf, there are schemas entries for most common filesystems but not for ext2 and a new subdir can't be added from within gconf-editor.  I naively added an ext2 entry to the storage schema by copying/pasting/editing one of the other filesystem entries but this has had no effect either and the new entry isn't shown in gconf-editor.

So the question is: how can I define mount behaviour for ext2/3 filesystems in a way that will apply a 000 umask?  Set like that, i don't care (i hope) who the owner is but it would be good if it were the user who actually mounted the disk.

Any ideas?  tia!

---

### Post by tlayton_at_work on 2007-11-19
What I did was let the ext3 partition be mounted by root, and then created a folder for my user with the proper ownership and permissions.  I figured this was probably safer than mounting the whole drive as my user.

So in my /etc/fstab, I put the following:

```
/dev/wd2 /media/WD_EXT3 ext3 defaults 0 0
```

Then, 

```

sudo mkdir /media/WD_EXT3/myuser
sudo chown myuser:myuser /media/WD_EXT3/myuser
sudo chmod 755 /media/WD_EXT3/myuser

```

Hope this helps.

---

### Post by CeeEss on 2007-11-19
Ah yes, but this is exactly what I''m trying to avoid :)  We mount/unmount as many as 50 disks per day on this wkstn so a painless and reliable automount is preferred.  I really want to avod the fstab route in any case. Thanks for the suggestion, though!

Given that this has been a headache of one sort or another since 2006, it would be useful for the developers of this software to look at getting it fixed once and for all!

thanks!

---

### Post by tsmets on 2007-12-03
My brand new ubuntu-server install has a similar ...
When plugging my external USB drive (which was correctly discovered on my Ubuntu-workstation), it does not see it !

\T,

---

