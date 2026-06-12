---
title: "How to move /usr to a new disk"
date: 2009-02-01
forum: General Help
---

### Post by sani07 on 2009-02-01
Hello

I use Xubuntu 8.04, but this is general question. I do not want to use any bootable CD.

I have single disk w/ two partitions /dev/sda1 (/) and /dev/sda2 (swap).
As the partition /dev/sda1 runs out of space, I got a new disk with partiton /dev/sdb1.

I want to move all files from directory /usr to a /dev/sdb1 so that all user permissoins are preserved.

How can I achieve this:
1./ Copy completely all file /usr/*.* to partition /dev/sdb1
2./ Delete the current /usr/*.*
3./ Mount /dev/sdb1 under /usr.


Alexander

---

### Post by ilrudie on 2009-02-01
> **sani07 said:**
> Hello

I use Xubuntu 8.04, but this is general question. I do not want to use any bootable CD.

I have single disk w/ two partitions /dev/sda1 (/) and /dev/sda2 (swap).
As the partition /dev/sda1 runs out of space, I got a new disk with partiton /dev/sdb1.

I want to move all files from directory /usr to a /dev/sdb1 so that all user permissoins are preserved.

How can I achieve this:
1./ Copy completely all file /usr/*.* to partition /dev/sdb1
2./ Delete the current /usr/*.*
3./ Mount /dev/sdb1 under /usr.


Alexander

Its probably a better idea to move /home to another disk because thats where all your personal files should be and thats usually where most of the size in a file system ends up on a PC.  To do this you will want to:
1: put a file system (ext3, reiserfs, ...) of some sort onto the new disk.
2: mount this new file system to /mnt
3: sudo cp /home/* /mnt
4: reboot into single user mode (I think its usually called admin or rescue mode under grub) which doesn't use /home because root's home is /root.
5: mv /home /home2
6: mkdir /home
7: edit /etc/fstab and change it so it uses uses the new file system on the new disk as /home
8: reboot
9: df -h to ensure its actually using the new disk as /home
10: only once you are sure the new disk is actually being used as /home should you consider erasing /home2

Most likely to move /usr you will have to boot from cd.  Single user mode will almost certainly require files from /usr so you wont be able to move it around.  Also note that if you move /usr to another disk and that disk fails you will be anable to boot whereas if you lost /home you would still be able to boot into rescue mode and try fixing the system.

---

### Post by sani07 on 2009-02-01
Hello Ilrudie

Thanks for your reply. I appreciate it. My PC is kind of experimental, I have almost nothing in home directory.
If I want to install Oracle XE database from debian package, I get error that there is not enough space in dirtectory /usr.

Therefore I need to move /usr.

In the single user mode are files from /usr still in use? How can I check it out?

How can I find out what files are open on Linux system?
Does the comand cp also copy file system permissions?
Alex

---

### Post by ilrudie on 2009-02-02
> **sani07 said:**
> Hello Ilrudie

Thanks for your reply. I appreciate it. My PC is kind of experimental, I have almost nothing in home directory.
If I want to install Oracle XE database from debian package, I get error that there is not enough space in dirtectory /usr.

Therefore I need to move /usr. [COLOR=Red]Not necessarily... see below.[/COLOR]

In the single user mode are files from /usr still in use? How can I check it out? [COLOR=Red]lsof | grep "/usr"[/COLOR]

How can I find out what files are open on Linux system? [COLOR=Red]fuser or lsof[/COLOR]
Does the comand cp also copy file system permissions? [COLOR=Red]try adding the flag --preserve=all [/COLOR]
Alex

Is /usr currently it's own separate mount point?  If its currently part of the / mount point (which it probably is) you can probably create space by cleaning up or moving /var (or any number of other directories that are also using space on the / mount point).  You could also consider not moving /usr but instead making a separate mount point for /usr/oracle (or wherever Oracle XE is meant to be installed) on the new disk.  Also you can run the following command to get an idea where the bulk of your disk use is.  Playing with --max-depth can get you more detail and removing it entirely will show you a ton of detail (possibly more than you need or want).
```
sudo du -k --max-depth=1 / | sort -nr
```

---

### Post by sani07 on 2009-02-06
Hello Ilrudie

Thanks very much for all your ideas. I will try them all.

I really appreciate your help.

Cheers.

Alexander

---

