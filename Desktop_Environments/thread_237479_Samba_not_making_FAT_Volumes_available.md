---
title: "Samba not making FAT Volumes available"
date: 2006-08-16
forum: Desktop Environments
---

### Post by ngms27 on 2006-08-16
Hi,

I've installed Dapper on a different partition and set up samba and imported smb.conf from my Breezy install.

For some reason Windows clients cannot see my FAT drives but can see my EXT3 ones.

Any ideas?

---

### Post by DoctorMO on 2006-08-16
The only thing I can suggest is:

1) Check that the FAT32 drives are mounted correctly
2) Check the permissions that the file systems mount as
3) Check that samba is correctly set up on this new machine, the location of the mount point may have changed.

There is no logical reason why samba would ignore a FAT32 drive since samba doesn't even know the FAT32 drive exists all it sees is the simple file system.

---

### Post by ngms27 on 2006-08-16
Well I can read and write to them from within Dapper though they appear on the Desktop with the Volume Name which they didn't do in Breezy.

Still not sure what the problem maybe

---

### Post by ngms27 on 2006-08-16
Um the Volumes are browsable, but it says I don't have permission when I try and access the drives.

---

