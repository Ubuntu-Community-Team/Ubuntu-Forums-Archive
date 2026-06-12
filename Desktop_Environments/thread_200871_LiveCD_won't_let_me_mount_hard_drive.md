---
title: "LiveCD won't let me mount hard drive"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Albi on 2006-06-20
It shows it under the computer, but whenever I double click it, it shows:

---

### Post by aysiu on 2006-06-20
Double-click mounting isn't happening in Ubuntu.
Knoppix'll do it. Ubuntu won't. Don't ask me why.

Is this a Linux or Windows partition? What's its location--/dev/hda1? /dev/hdb2?

---

### Post by Albi on 2006-06-20
It's a 120GB NTFS WIndows XP drive.  I'm using the LiveCD, but I'm planning on making a 15GB Ubuntu partition soon.
And it's location is: /dev/hda1

---

### Post by aysiu on 2006-06-20
So are you trying to mount it to recover data off it?

Let me just let you know two things:
1. You don't need to mount it to make a Ubuntu partition. In fact, you can resize a partition only if it's *unmounted*.
2. NTFS is read-only if mounted properly. There's no modifying files--only copying the files off the drive.

That said, this is how you mount it: ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222
```

---

### Post by Albi on 2006-06-20
[QUOTE=aysiu]So are you trying to mount it to recover data off it?

Let me just let you know two things:
1. You don't need to mount it to make a Ubuntu partition. In fact, you can resize a partition only if it's *unmounted*.
2. NTFS is read-only if mounted properly. There's no modifying files--only copying the files off the drive.

That said, this is how you mount it: ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222
```[/QUOTE]
Yes, I'm aware that NTFS is read only.  The reason I'm mounting it is to see how well my games run with WINE
Thx for the help.

---

