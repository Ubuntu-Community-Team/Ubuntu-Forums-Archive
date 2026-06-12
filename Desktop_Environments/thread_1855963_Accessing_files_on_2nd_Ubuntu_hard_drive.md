---
title: "Accessing files on 2nd Ubuntu hard drive"
date: 2011-10-07
forum: Desktop Environments
---

### Post by TotalLinux on 2011-10-07
Hello all,
I've looked through various threads but my issue isn't replicated on any of them.
I have a new system (running Lucid 10.04) and today I have added the old hard drive (with all of the files on there that I wish to transfer to the new main drive, bookmarks, e-mails, docs, etc.). The old hard drive is also running Lucid 10.04
sudo fdisk -l reads OK, I can mount the drive without any problem and I can see the folders within the mounted drive but am unable to access the data held within. I'm naturally reluctant to start thrashing around at any old attempt to access the files in case I accidentally wipe part or all of them.
Any assistance greatly appreciated. Thanks in advance.
Regards,
TotalLinux

---

### Post by Jonathan L on 2011-10-07
> **TotalLinux said:**
> Hello all,
I've looked through various threads but my issue isn't replicated on any of them.
I have a new system (running Lucid 10.04) and today I have added the old hard drive (with all of the files on there that I wish to transfer to the new main drive, bookmarks, e-mails, docs, etc.). The old hard drive is also running Lucid 10.04
sudo fdisk -l reads OK, I can mount the drive without any problem and I can see the folders within the mounted drive but am unable to access the data held within. I'm naturally reluctant to start thrashing around at any old attempt to access the files in case I accidentally wipe part or all of them.
Any assistance greatly appreciated. Thanks in advance.
Regards,
TotalLinux

Hi Total

The trick with this kind of thing is make sure you mount it readonly.

By "can't access" I'm guessing you can't even read or browse any of the folders; typically this is caused by different user ID numbers on disk compared to the new system.

You check your current user id by 'id' or looking in /etc/passwd
You check the id numbers on the disk by 'ls -ln'

The classical way to deal with this is copy the old disk into somewhere on the new one as root, and then move things around and change the ownership for whole trees (with 'chown -R') or just for files owned by particular user (classically with find -u 123, but Gnu chown has an extension --from for doing exactly this).

Hope that's of use.

Kind regards,
Jonathan.

---

