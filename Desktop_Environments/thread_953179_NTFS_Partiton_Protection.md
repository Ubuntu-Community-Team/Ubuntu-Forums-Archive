---
title: "NTFS Partiton Protection"
date: 2008-10-19
forum: Desktop Environments
---

### Post by Keymaster on 2008-10-19
I am in the process of converting a Windows XP machine to Ubuntu 8.04.  While selectively copying over specific files from the NTFS partition over the course of the upcoming weeks, I want to prevent regular users from mounting the partition.  It appears that anyone can mount the partition, by clicking on it in the Places menu.  The partitions do not show up in /etc/fstab /etc/mtab. Regular non-sudoers can mount it.  This is a problem as each user on ubuntu has a corresponding Windows XP account with private documents accessible to everyone else who can mount it.  How come Hardy allows this to happen.  The previous Ubuntu required sudo to mount NTFS, and it also appeared in fstab.  This is quite important.  Thanks

---

### Post by ztrange on 2008-10-19
Check te /etc/fstab where you can find the configuration of the filesystems mounted in your pc. There you can put some option like nouser to prevent non-root users to mount some partition.

A good explanation of the fstab file is [here]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by Keymaster on 2008-10-20
It's using fuse to mount the partition so it doesn't appear in fstab.  I can't disable fuse for these users, as they need it touse truecrypt.

---

### Post by Keymaster on 2008-10-23
bump
Come on, someone must have a solution.  It would really help.

---

### Post by Keymaster on 2008-10-30
Bump again :(
I could really use a solution

---

