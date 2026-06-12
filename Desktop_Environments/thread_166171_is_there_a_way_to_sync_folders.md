---
title: "is there a way to sync folders?"
date: 2006-04-25
forum: Desktop Environments
---

### Post by groggyboy on 2006-04-25
i completely reinstalled ubuntu the other day (well, actually i upgraded to dapper beta).  but anyways, i thought my 'documents' folder was nicely safe in a seperate /home partition.  something messed up, and when the fresh install was finished, my /home partition was empty.  luckily, i had backed it up on my roommate's computer.  my other document partition, a FAT32 partition with all my music and videos, was untouched.

i was really freaked out by this, so i'm wondering: is there a program or script or something that would automatically syncronize the contents of a 'documents' folder in my /home partition and a 'documents' folder in my FAT32 share partition?  something so that if i added a file to either folder, the other folder would automatically receive a copy of it?  this way, if i ever again borked one of those partitions, the other would be an up-to-date duplicate.

any ideas?

cheers,
groggyboy

---

### Post by Stewart on 2006-04-25
Mirrordir might be what your looking for. This is some of the man page. Its in the Utilities (universe) repo.

_____________________________________________________________________
 mirrordir is a set of useful utilities for manipulating and mirroring directories. Included is also
       the  command pslogin - an alternative to ssh(1), and forward-socket(1) for forwarding arbitrary TCP
       socket connections over encrypted secure channels.

       mirrordir copies files that are different between the directories control and mirror to the  direc&#8208;
       tory  mirror.  Files  whose modification times or sizes differ are copied. File permissions, owner&#8208;
       ships, modification times, access times (only if --access-times is used), sticky bits,  and  device
       types  are  duplicated.  Symlinks  are duplicated without any translation. Symlink modification and
       access times (of the symlink itself, not the file it points to)  are  not  preserved.  Hard  linked
       files are merely copied. Creation times cannot be set with Unix as far as I can see.

       mirrordir is a DANGEROUS command because files or directories that exist in mirror that don’t exist
       in control are deleted. If control is entirely empty, then all files and directories in mirror will
       be  deleted. If mirror is entirely empty, then all files and directories in control will be copied.

       In short, mirrordir forces mirror to be an exact replica of the directory  tree  control  in  every
       possible detail suitable for purposes of timed backup. It naturally descends into subdirectories to
       all their depths. mirrordir tries to be as efficient as possible  by  making  the  minimal  set  of
       changes necessary to mirror the directory.

---

