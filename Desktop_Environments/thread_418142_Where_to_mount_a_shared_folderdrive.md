---
title: "Where to mount a shared folder/drive"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Jhongy on 2007-04-22
Hello,

I currently have a couple of extra hard disks - one for backups and one for general file storage.

I want to share these - or subfolders in these, between users of this computer.

They're currently mounted in /mnt/docstor and /mnt/backups, and I've put links in my homw directory... however, where's the usual place to present such folderrfs/drives for all users? /usr/share??? or... ?

---

### Post by Pobega on 2007-04-22
By default Debian based distributions use the /media folder for storage, even though it is historically /mnt where you mount external media to. But all in all both work, and it's up to you to do whatever feels comfortable.

---

### Post by dcstar on 2007-04-22
> **Jhongy said:**
> Hello,

I currently have a couple of extra hard disks - one for backups and one for general file storage.

I want to share these - or subfolders in these, between users of this computer.

They're currently mounted in /mnt/docstor and /mnt/backups, and I've put links in my homw directory... however, where's the usual place to present such folderrfs/drives for all users? /usr/share??? or... ?

If you want to share them then you may have permission issues with things in your own home directory, you can really put links (or mount points) anywhere, even the root directory - do whatever is convenient for you.

---

### Post by Jhongy on 2007-04-22
Thanks..


I've mounted them in mnt as they're internal hdds

In a 'normal' unix-based system, where do shared files go? I was just interested as to whether there was some sort of standard.

For permissions, I was planning on using ACL.

---

