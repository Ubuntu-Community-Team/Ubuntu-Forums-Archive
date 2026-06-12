---
title: "external hdd permissions multiple users"
date: 2009-01-19
forum: General Help
---

### Post by DasLemm on 2009-01-19
Hey, i've got an external hdd that i keep my media on and such. and it works fine whenever i need to use it, more specifically it works fine with whoever mounts it first. But when someone else logs into the comp, they get denied access to read the drive. how can i set the proper permissions for this drive with out chown or chmod (neither work)
When looking at the user privileges, 'Allow access to external storage devices' is checked positive.
um, ubuntu 8.10 x64
external drive is fat32

thanks in advance

---

### Post by DasLemm on 2009-01-20
Any help would be appreciated...

---

### Post by CrusaderAD on 2009-01-20
Did you try:

sudo chmod 777 foldername

---

### Post by DasLemm on 2009-01-20
I have tried chmod, as well as chown. the terminal sits there as if it's working, but when it returns to a prompt the folders are still not accessible by anyone who didn't mount the drive.

---

### Post by dcstar on 2009-01-20
> **DasLemm said:**
> Hey, i've got an external hdd that i keep my media on and such. and it works fine whenever i need to use it, more specifically it works fine with whoever mounts it first. But when someone else logs into the comp, they get denied access to read the drive. how can i set the proper permissions for this drive with out chown or chmod (neither work)
When looking at the user privileges, 'Allow access to external storage devices' is checked positive.
um, ubuntu 8.10 x64
external drive is fat32

thanks in advance

Firstly put a Label on the partition - this way it will always be mounted using the label name.

Then make an entry for it in /etc/fstab - the easiest way to do this is by using the **pysdm **package, then System-Administration-Storage Device Manager. You should be able to then set the fstab line to allow use by all users.

---

### Post by CaesarLike on 2009-01-20
Just an idea, not sure if it will work, but -

Are you chown/chmod the directory that ubuntu auto creates to mount the drive when you plug in the drive?

Have you tried creating a directory to mount the drive to each time such as:

/media/extdrive

then chmod the directory as 777

Then when you want to mount the drive, don't let ubuntu auto mount it, or unmount it if it does.  Use the terminal to mount the drive to the directoy you created.  You could also try putting all the users who want to access the drive into the same group, and make that group the group owner for the directory.
Of course, if all else fails just use a NAS to store the files on.

---

### Post by DasLemm on 2009-01-21
It looks like pysdm did the trick
thanks alot!:KS

---

### Post by jerome1232 on 2009-01-21
> **dcstar said:**
> Firstly put a Label on the partition - this way it will always be mounted using the label name.

Then make an entry for it in /etc/fstab - the easiest way to do this is by using the **pysdm **package, then System-Administration-Storage Device Manager. You should be able to then set the fstab line to allow use by all users.

Neat I didn't realize there was a gui for editing the fstab (I've been thinking there should be one due to the number of questions in this area)

Normally I would slap a "thanks" on your post :)

---

