---
title: "Hardy: Trash never works (64-bit)"
date: 2008-05-20
forum: Desktop Environments
---

### Post by konungursvia on 2008-05-20
I upgraded as of Hardy Beta 5 in March, and as a result, many apps required root to run at all until I reinstalled them and/or did a chmod and chown to set permissions to standard values. As yet, nothing ever moves to trash, though this seems not to be a problem for those who upgraded later, in April.

Does anyone know now to fully reset and fully reinstall the trash applet and everything related to trash? I always get the pop-up "Cannot move to trash. Delete? Delete All?" etc.

A corollary of this question is, is this the right set of permissions?

drwxr-xr-x 3 peter users 4096 2008-03-24 11:32 /home/peter/.local/share/Trash/files

That's what I have now.

Many thanks and muchas gracias.

---

### Post by noynac on 2008-05-20
I received that message with ntfs and vfat drives and found a solution. Your situation appears different, but I thought I would post what I did just in case it might be of assistance to you or others. 

What I did was:

1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.

Upon completion of the above, deleted files are placed in a directory named files within the .Trash-1000 directory, and the Ubuntu desktop trash icon shows the deleted files.

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

---

### Post by VMC on 2008-05-20
> **konungursvia said:**
> 
A corollary of this question is, is this the right set of permissions?

drwxr-xr-x 3 peter users 4096 2008-03-24 11:32 /home/peter/.local/share/Trash/files

Many thanks and muchas gracias.I have the same. Also under Trash there is another directory named info, with a bunch of zero length files.

And in the root directory there is a file named .Trash-0 (/.Trash-0)

---

### Post by konungursvia on 2008-05-20
Ok, but it's not a Microsoft drive format, it's my ext3 /home/ directory. Do I still try that?

---

### Post by noynac on 2008-05-20
> **konungursvia said:**
> Ok, but it's not a Microsoft drive format, it's my ext3 /home/ directory. Do I still try that?

No! The fix I posted only works with ntfs and vfat drives. Sorry I couldn't be of help--perhaps someone else will have a suggestion.

---

### Post by konungursvia on 2008-05-24
So trash is not part of a package I can reinstall?

---

### Post by konungursvia on 2008-05-28
:( I wish I knew...

---

### Post by konungursvia on 2008-06-08
Trash still does not work!

---

### Post by konungursvia on 2008-06-15
Trash still does not work in hardy 64 bit for me.

---

