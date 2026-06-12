---
title: "PCManFM Can't Send Files to Trash"
date: 2011-12-12
forum: Desktop Environments
---

### Post by dodle on 2011-12-12
If I try to delete files to the trash from PCManFM I get an error dialog that says this:

> Some files cannot be moved to trash can because the underlying file systems don't support this operation.
Do you want to delete them instead?

I can move files to the trash from the desktop just fine. I am using Lubuntu 11.04 but I tried installing the version from the 11.10 repository, same problem. I understand that PCManFM uses gvfs-trash for this operation. When I try it from the command line I get this:

```
$ gvfs-trash blah.txt
Error trashing file: Unable to find or create trash directory
```

So it looks like the problem lies in gvfs-trash. My trash folder is intact in "/home/jordan/.local/share/Trash".

**----- EDIT -----**

Just figured out a piece of the puzzle. It only has problems deleting files from a second partition that I have on my HD. Anything from my main partition can be moved to the trash without problems. My second partition is formatted to Ext2 and is mounted to /media/Data. There is a folder in the root of the partition called .Trash-1000, I assume the 1000 is for my user id number. I tried deleting this folder to see if it would remake it and fix the problem, but I get an error with that as well:

```
:/media/Data$ sudo rm -r .Trash-1000
rm: cannot remove `.Trash-1000/info/db.3.trashinfo': Input/output error
rm: cannot remove `.Trash-1000/info/pool.3.trashinfo': Input/output error
rm: cannot remove `.Trash-1000/files': Input/output error
rm: cannot remove `.Trash-1000/expunged/3948227900/version': Input/output error
```

**----- EDIT -----**

Found an answer [here](http://ubuntuforums.org/showthread.php?p=7105357). I unmounted the partition and ran "sudo e2fsck /dev/sda3":

```
:~$ sudo e2fsck /dev/sda3
e2fsck 1.41.14 (22-Dec-2010)
Data contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'version' in /.Trash-1000/expunged/3948227900 (1892355) has deleted/unused inode 1892366.  Clear<y>? yes

Entry 'files' in /.Trash-1000 (2498561) has deleted/unused inode 2514945.  Clear<y>? yes

Entry 'db.3.trashinfo' in /.Trash-1000/info (2506753) has deleted/unused inode 2506777.  Clear<y>? yes

Entry 'pool.3.trashinfo' in /.Trash-1000/info (2506753) has deleted/unused inode 2506778.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 1859595 ref count is 8, should be 6.  Fix<y>? yes

Inode 2498561 ref count is 5, should be 4.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  -7569945 -(10298010--10298011)
Fix<y>? yes

Free blocks count wrong for group #231 (32130, counted=32131).
Fix<y>? yes

Free blocks count wrong for group #314 (23495, counted=23497).
Fix<y>? yes

Free blocks count wrong (4143774, counted=4143777).
Fix<y>? yes

Inode bitmap differences:  -1892366 -(2506777--2506778)
Fix<y>? yes

Free inodes count wrong for group #231 (8185, counted=8186).
Fix<y>? yes

Free inodes count wrong for group #306 (8188, counted=8190).
Fix<y>? yes

Free inodes count wrong (3503102, counted=3503105).
Fix<y>? yes


Data: ***** FILE SYSTEM WAS MODIFIED *****
Data: 3071/3506176 files (8.2% non-contiguous), 9872479/14016256 blocks
```

Everything works fine now.

---

