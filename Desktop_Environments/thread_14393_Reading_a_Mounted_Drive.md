---
title: "Reading a Mounted Drive?"
date: 2005-02-07
forum: Desktop Environments
---

### Post by ZakZak on 2005-02-07
When I do "mount /dev/sdb1 /home/zak/sdb1" I get "only root can do that".

So, I tried "sudo mount /dev/sdb1 /mnt/sdb1" which works.  However, when I try to access anything in /mnt/sdb1 as my zak user (even a simple "ls /mnt/sdb1"), I get "Permission denied".

What's the correct way to mount another drive and have it be accessible to non-root users?

Thanks!
-Zak

---

### Post by ilari on 2005-02-07
[QUOTE=ZakZak]When I do "mount /dev/sdb1 /home/zak/sdb1" I get "only root can do that".

So, I tried "sudo mount /dev/sdb1 /mnt/sdb1" which works.  However, when I try to access anything in /mnt/sdb1 as my zak user (even a simple "ls /mnt/sdb1"), I get "Permission denied".

What's the correct way to mount another drive and have it be accessible to non-root users?

Thanks!
-Zak[/QUOTE]
 You can add a new line for the drive to /etc/fstab. Try for example the following (replace the strings in brackets with real values):

/dev/<device> /mnt/<dirname> <filesystem> noauto,users,uid=0,gid=0,umask=0 0 0

Then you can mount it as a normal user by 'mount /mnt/<dirname>'

---

### Post by Adrenal on 2005-02-07
sudo mount /dev/sdb1 /home/zak/sdb1 -t (whatever format it is, maybe ntfs) -r -o uid=zak

---

