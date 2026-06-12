---
title: "fsck doesn't want to perform filesystem fix"
date: 2009-01-22
forum: General Help
---

### Post by markovcd on 2009-01-22
I have Ubuntu 8.10 Wubi. Today my system hanged so I restarted it by pressing reset button. After next launch fsck wanted to fix partition but had the following error:

```

 sudo fsck -p '/media/disk/ubuntu/disks/root.disk' 
fsck 1.40.8 (13-Mar-2008)
/media/disk/ubuntu/disks/root.disk contains a file system with errors, check forced.
Error reading block 393218 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/media/disk/ubuntu/disks/root.disk: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

So i ran it:

```

sudo fsck '/media/disk/ubuntu/disks/root.disk' 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/media/disk/ubuntu/disks/root.disk contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 393218 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 393218 (Attempt to write block from filesystem resulted in short write) while getting next inode from scan.  Ignore error<y>? yes

Error reading block 393219 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 393219 (Attempt to write block from filesystem resulted in short write) while getting next inode from scan.  Ignore error<y>? yes

Error reading block 393220 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? 

```

...and so on. What should i do now?

---

