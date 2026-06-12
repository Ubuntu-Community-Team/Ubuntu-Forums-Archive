---
title: "A wall of separation between users?"
date: 2008-01-23
forum: Desktop Environments
---

### Post by mount_evans on 2008-01-23
So far mine is the only "account" on my Ubuntu installation.  I would like to create others, but I want the users to have privacy from each other.  It seemed in the past (under SuSE) that the default was for every user to be able to read every other user's files.  Sure, it was possible to change the permissions on one's files, but you had to keep doing it for any new files that got created later.  Or so I thought, anyway.

So, what is the easiest way to prevent any one user from reading any other user's files without going into superuser mode?  I was thinking of creating a separate "group" for each user.  Would that do it? 

This would only apply to everybody's home directory, I hope.

---

### Post by jeffus_il on 2008-01-23
That's been happening automatically for me on recent installs, e.g. user mount_evans group mount_evans, probably for that very reason.

Nice Signature!

---

### Post by gastur on 2008-01-23
Try playing with umask in /etc/skel files.

---

### Post by petteriIII on 2008-01-24
At least separation of mounted filesystems is adressed in Hardy (8.04). It seems that it is not fine-grained enough and don't separate users too well, but time will tell.

---

### Post by Whiffle on 2008-01-24
Simply change the permissions on their home directories, to where only the owner can read/write/execute them.

---

