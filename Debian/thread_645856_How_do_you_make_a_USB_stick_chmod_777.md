---
title: "How do you make a USB stick chmod 777?"
date: 2007-12-20
forum: Debian
---

### Post by jingo811 on 2007-12-20
My mother just got an 1 GB USB stick to play with.  Unlike my 128 MB USB stick where anybody can store stuff on it.  My mothers 1 GB stick requires ppl to become root in order to store things.  That's not right :confused:

I tried to solve things by doing this but nautilus doesn't respond at all even when I do it in terminal.  My hope was to tick all the permissions options so that anybody could store things on this stick.
```
Alt-F2
gksudo nautilus
```

Then I tried to just simply chmod it but nothing changes.
```
$ su -
$ chmod 777 /dev/sda1
$ chmod 777 /media/sda1
```

What the correct way of making an USB memory stick accessible to anybody, anywhere, anytime?
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         121      971901    b  W95 FAT32
debian:~#

```

---

### Post by jingo811 on 2007-12-21
Hmmm it seems Ubuntu Feisty isn't affected by permission problems when accessing a USB stick.  Only Debian Etch seems to require ppl to become root in order to access it.
Well problem solved recommend Ubuntu for your mothers not Debian :)

---

