---
title: "FAT permission problem"
date: 2005-10-13
forum: Desktop Environments
---

### Post by fnando on 2005-10-13
Hello There!

I'm mounting a FAT partition on start-up. I could write/read that partition and everything was just fine until yesterday! But now, everytime I try to write something I receive the following message:

> 
Error while copying to "/media/win_e".
You do not have permissions to write to this folder.


My fstab has the following line ([http://ubuntuguide.org/#automountfat):](http://ubuntuguide.org/#automountfat):)

```

/dev/hdb6       /media/win_e  vfat    iocharset=utf8,umask=000   0       0

```

Any tip? This is sux!

Thanks!

---

### Post by frodon on 2005-10-13
Add the **users** parameter it will allow you to write/read on your partition as a simple user :```
/dev/hdb6       /media/win_e  vfat    iocharset=utf8,**users**,umask=000   0       0
```

---

### Post by fnando on 2005-10-13
Thanks frodon! I'll try it that when I get home! ;)

---

### Post by manicka on 2005-10-14
I use this one so that the mounted partition doesn't appear on my desktop

```
/dev/hdb6       /media/win_e   vfat     defaults,rw,umask=000 0 0
```

---

### Post by fnando on 2005-10-14
[QUOTE=manicka]I use this one so that the mounted partition doesn't appear on my desktop

```
/dev/hdb6       /media/win_e   vfat     defaults,rw,umask=000 0 0
```[/QUOTE]


Hummm... cool! 

Guess what? 
Yesterday when I came home, the partition had write permission as before.... so f**k strange.... but thanks anyway.

---

