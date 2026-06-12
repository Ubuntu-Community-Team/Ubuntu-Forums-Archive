---
title: "[SOLVED] Cannot change permissions on a FAT32 partition in Nautilus with root privile"
date: 2008-12-23
forum: General Help
---

### Post by Piraja on 2008-12-23
Dear all,

I just encountered a curious problem (possibly a bug?), described in the title of this thread. After copying files from a FAT32 "storage" partition (henceforth referred to as /media/FAT32_100GB) into my son's home directory on his user account (i.e. logged in with his user name) the owner of the whole directory had changed: now my son had exclusive ownership of the whole fat32 partition, so that I could not even access it without root privileges. 

Yet, even doing gksudo nautilus I could not chown; then I went to VT and tried sudo chown -R piraja:piraja /media/FAT32_100GB/ but to no avail: Operation not permitted. I rebooted and discovered that I had regained the ownership of /media/FAT32_100GB again, as it should be since I'm the main user of this machine. But, as I logged into X and checked the permissions of the partition in Nautilus (gksudo nautilus) I could not effect any change upon the "Group" and "Others" permissions — even with root privileges, which does not seem to make sense.

Could this be a bug? Could it be caused by inter-fs transfers (i.e. from fat32 to ext3)?

Thanks in advance for any answers & comments,

with Yuletidish regards

Piraja

---

### Post by jrusso2 on 2008-12-23
Fat 32 is not capable of having permissions.  You need NTFS for that so when you moved the files to ext 3 it changed the owner.

As Microsoft is fond of saying its not a bug its a feature.  Windows originally was a single user operating system.

---

### Post by Piraja on 2008-12-23
Thanks — I had never before encountered this, maybe because until now I had copied files from the fat32 partition with my own user rights and not e.g. my son's. Henceforth, I will be even less enthusiastic about "leaving the filesystem."

---

