---
title: "Can't access NTFS partition"
date: 2005-10-15
forum: Desktop Environments
---

### Post by r@mix on 2005-10-15
My (win XP) NTFS partition is well detected and mounted but in read-only mode and I can't access to it with a normal user. I can't change the permissions "because it's a read-only disk".
I can't even change the owner, for the same reason. The options in /etc/fstab are "defaults", as for the other (FAT32) windows partition.
Is it normal ?

---

### Post by Lord Illidan on 2005-10-15
Sadly, NTFS support in Linux is strictly read only.. Writing is considered very experimental, and can have the side effect of wiping the registry.

In the /etc/fstab, I suggest you use this :

/dev/hdc1       /media/windows  ntfs    nls=utf8,umask=0222     0       0

Replace the /dev/hdc1 with whatever you have..

---

### Post by r@mix on 2005-10-15
Thank you very much for your help. I knew that NTFS is just read-only in Linux but I didn't understand how to access the partition with another user than root.
Why isn't set the right umask during the installation ? It would be easier.

---

### Post by aysiu on 2005-10-15
If you want it automatic, use Mepis or Knoppix.
If you don't mind (one time only) editing your /etc/fstab and copying and pasting a line, Ubuntu's got a lot else going for it.

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Hairy_Palms on 2005-10-15
if that doesnt work then change it to umask=000
thats what i had to do.

---

