---
title: "can't change permissions on second hard drive"
date: 2008-12-02
forum: General Help
---

### Post by rusty_jones on 2008-12-02
the location is HD: /media/sdb1 folder is musica. The permissions for musica is root although I created it. I have tried gksudo nautalis to change permissions and it will not allow me. 

error i get is 'the owner cannot be changed" error setting owner: Operation not permitted" I have tried a variety of suggestion from previous forum recommendations with same results. 

Can anyone offer some suggestions.

Rusty

---

### Post by capitalistpiglet on 2008-12-02
Try changing the owner from the command line
```
sudo chmod -R username musica
```
And then possibly chmod the dir for good measure.
```
sudo chmod -R 755 musica
```
If that doesn't work how is the drive mounted? what is the output for that drive from the command mount ?

---

### Post by rusty_jones on 2008-12-02
first command i got:  invalid mode: `stan'

second command:  cannot access `musica': No such file or directory


> /dev/sdb1 on /media/sdb1 type vfat (rw,iocharset=utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)



Rusty

---

### Post by rusty_jones on 2008-12-03
Does anyone have a solution for this?

Rusty

---

