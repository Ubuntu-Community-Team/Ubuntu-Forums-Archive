---
title: "fs error"
date: 2005-12-28
forum: General Help
---

### Post by djlosch on 2005-12-28
apparently i have some dependency error somehow, so i try and apt-get -f install, and i get:
```
The following packages have unmet dependencies:
  libdbi-perl: Depends: libplrpc-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
then i check an apt-get install libdbi-perl, and it turns out the manpages dir that it is trying to overwrite has an IO error.
```
root@io:/usr/share/man/man3# ls
ls: reading directory .: Input/output error
```
i'm using reiser on hda1 (where the man page is).

any ideas on how to fix this?  i can't use apt-get at all til i fix this, and i'd rather not have to re-install (setting up icecast was a bitch)

---

### Post by zoiks on 2005-12-28
The only times I've had I/O errors was when a hard disk was physically going bad.  You should consider backing up your important data immediately and doing an fsck on the partition.  I could be wrong, though.

---

### Post by sciurus on 2005-12-29
AN EXAMPLE OF USING reiserfsck
       1. You think something may  be  wrong  with  a  reiserfs  partition  on
       /dev/hda1 or you would just like to perform a periodic disk check.

       2.  Run reiserfsck --check --logfile check.log /dev/hda1. If reiserfsck
       --check exits with status 0 it means no errors were discovered.

       3. If reiserfsck --check exits with status 1 (and reports about fixable
       corruptions)  it  means  that  you  should run reiserfsck --fix-fixable
       --logfile fixable.log /dev/hda1.

       4. If reiserfsck --check exits with status 2 (and reports  about  fatal
       corruptions)  it  means that you need to run reiserfsck --rebuild-tree.
       If reiserfsck --check fails in some way you should also run  reiserfsck
       --rebuild-tree,  but  we  also  encourage  you  to submit this as a bug
       report.

       5. Before running reiserfsck --rebuild-tree, please make  a  backup  of
       the  whole  partition before proceeding. Then run reiserfsck --rebuild-
       tree --logfile rebuild.log /dev/hda1.

       6. If the reiserfsck --rebuild-tree step fails or does not recover what
       you  expected,  please  submit  this as a bug report. Try to provide as
       much information as possible including your platform and  Linux  kernel
       version. We will try to help solve the problem.

---

### Post by werty on 2006-01-03
Hi
I needed to check my reiserfs partition and did 'fsck'...
but it returned this message - 
" Partition /dev/sda9 is mounted with write permissions, cannot check it "
what should i do...
thanks

---

### Post by zoiks on 2006-01-03
You can remount a partition with the option "-o remount,ro" to remount the drive read-only.

---

### Post by werty on 2006-01-04
where should i use the command..
can you post the full command plz...
thanks

---

### Post by zoiks on 2006-01-08
At the command line.  The command would look like

mount -o remount,ro <mount point>

If it's just an external storage device, you could also just unmount it (using the umount command) and fsck it directly.

---

### Post by werty on 2006-01-16
i entered 
"  sudo mount -o remount,ro /dev/sda9 "
and the terminal returned
" mount: / is busy "
What should i do...

---

