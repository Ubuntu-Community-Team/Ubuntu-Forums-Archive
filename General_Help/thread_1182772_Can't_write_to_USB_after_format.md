---
title: "Can't write to USB after format"
date: 2009-06-09
forum: General Help
---

### Post by unmole on 2009-06-09
I formatted my USB device (ancient 512MB ipod shuffle) to ext3 using Gparted. after that, I am unable to write to it unless I am root. How do I change it so that I can write to it without becoming root ?




P.S. I don't care about not being able to use it as an ipod but I am trying to install Slax (A mini live distro) on it.

---

### Post by ptn107 on 2009-06-09
Pop open a terminal (Applications -> Accessories -> Terminal) and type:
```
ls -l /media/
```

Paste the output here.

---

### Post by unmole on 2009-06-09
> **ptn107 said:**
> Pop open a terminal (Applications -> Accessories -> Terminal) and type:
```
ls -l /media/
```Paste the output here.

```
 user@ubuntu:~$ ls -l /media/
total 5
lrwxrwxrwx 1 root root    6 2009-05-19 15:58 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-05-19 15:58 cdrom0
drwxr-xr-x 3 root root 1024 2009-06-09 20:29 disk 
```

---

### Post by dmizer on 2009-06-09
You'll need to change ownership of the drive after formatting.

Something like this:
```
sudo chown -R unmole:unmole [COLOR="Red"]/ipod/mountpoint[/COLOR]
```
Change "[COLOR="Red"]/ipod/mountpoint[/COLOR]" to the actual mount location for your ipod (usually somewhere in /media).

---

### Post by unmole on 2009-06-09
Thanks a lot........that worked. :D In some other forum I found instructions to change permissions so it becomes writable by all users but I could not read the lost+found folder,changing the owner took care of it.

---

### Post by dmizer on 2009-06-09
> **unmole said:**
> Thanks a lot........that worked. :D In some other forum I found instructions to change permissions so it becomes writable by all users but I could not read the lost+found folder,changing the owner took care of it.

Keep in mind, that if you carry the USB stick to another linux machine, that you will again be unable to access the lost+found folder (different user = different permissions).

---

### Post by unmole on 2009-06-09
> **dmizer said:**
> Keep in mind, that if you carry the USB stick to another linux machine, that you will again be unable to access the lost+found folder (different user = different permissions).

Oh well,I will keep that in mind...But then again the folder is only for storing corrupted files when found during a filesystem check, right ?

---

### Post by unmole on 2009-06-09
Anyway thank you for your help.

---

