---
title: "cannot write to second hard drive"
date: 2009-05-11
forum: General Help
---

### Post by c/Kr3t on 2009-05-11
hello

i have recently installed a second hard drive and formatted it to ext4 but i cannot write to it.

i can mount and read it though.

how do i enable writing for my user?

thanks

---

### Post by Triptol on 2009-05-11
You first need to check how the drive is mounted:
```
mount
```
Check with you drive what options are set. If it is read-only you will see. If it is not read-only you probably have a rights problem. In that case check whether your user has write rights on the drive (by default only root can write to a drive).
If the drive is read-only it is important to check why it is read-only. Is it an option in your fstab?
If the drive is just mounted read-only you can remount it:
```
mount -o remount,rw /dev/foo /dir
```
(taken from the mount manual pages). /dev/foo is your drive, probably /dev/sdb1 and /dir is the directory where it is mounted.

---

### Post by c/Kr3t on 2009-05-11
i tried what you said but i still get permission denied when i try to drag a file onto the drive

i have it mounted and there is an icon my desktop. i can open it and see what's inside, i just can't copy or move anything into it

---

### Post by glotz on 2009-05-11
Became the owner of the disk```
sudo chown -R username:usergroup /path/to/disk
```
By default your usergroup is the same as your username

---

### Post by c/Kr3t on 2009-05-11
> **glotz said:**
> Became the owner of the disk```
sudo chown -R username:usergroup /path/to/disk
```
By default your usergroup is the same as your username

worked, thanks

---

### Post by glotz on 2009-05-11
You're welcome.

---

### Post by Wainorg on 2009-05-27
Had the same problem and your respons works, cheers.

---

### Post by glotz on 2009-05-27
Congrats for finding it! :)

---

