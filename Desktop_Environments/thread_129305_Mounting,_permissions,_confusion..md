---
title: "Mounting, permissions, confusion."
date: 2006-02-13
forum: Desktop Environments
---

### Post by pbaehr on 2006-02-13
Ok. I'm setting up a quick and dirty file server using samba. An entire physical hard drive will be shared in a small office. I want to be able to mount the drive so that anyone can read and write to it over the network. Security is not a big issue.

I have no problems configuring Samba to share a folder with those priveleges if I make a new folder myself. However, when I try to set permissions on the other hard drive (/mnt/fat32) it will not allow write access for anyone but "owner." Basically, the most permissions I can assign is rwxr-xr-x. I'm assuming this is a problem with the way it is mounted.

Here is the entry from fstab:
/dev/hdb1   /mnt/fat32   vfat   rw,user,auto   0   0

Am I doing something fundementally wrong here?

---

### Post by pbaehr on 2006-02-13
Never mind, I got it figured out. Posted too quick.

For anyone who's searching for a similar issue and finds this the correct fstab entry should be:

/dev/hdb1   /mnt/fat32   vfat   iocharset=utf8,umask=000   0   0

That did the trick perfectly.

---

