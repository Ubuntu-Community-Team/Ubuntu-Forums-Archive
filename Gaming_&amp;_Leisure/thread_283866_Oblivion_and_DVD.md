---
title: "Oblivion and DVD"
date: 2006-10-24
forum: Gaming &amp; Leisure
---

### Post by Zeek00 on 2006-10-24
I'm trying to install Oblivion using Cedega. When I put the Oblivion DVD in the DVD rom nothing really happens. I can't browse to the DVD like I could browse to any of my other game CD's. When I enter Cedega and try to mount it, it cannot mount it and I basically can't read the DVD.

I know its not a bad disk because it worked fine when I was running windows. I also understand that I need to download Oldblivion to actually run the game to get around some shading issues and Direct X 9. But Don't I need to install Oblivion from the DVD first then install OldBlivion? How do I fix my whole cannot read the DVD problem? I can watch normal DVDs using the drive but it will not read the game disk.

Thanks in advance,
Zeek

---

### Post by Zeek00 on 2006-10-24
When I try to browse to the DVDrom to read the Oblivion disk, this is what i get:

```

/media$ cd cdrom-1
bash: cd: cdrom-1: Permission denied

```

So how would I go about getting around it?

---

### Post by Zeek00 on 2006-10-25
No ideas?

---

### Post by Tycho on 2006-10-25
This happens to me too.

I right-click on the cd icon on the desktop and select mount.

Then I open a terminal and run 'gksu thunar' and then I can browse the disk.

If you are using ubuntu you might be able to try 'gksu nautilus' or something like that to browse it with root permissions.

---

### Post by Zeek00 on 2006-10-28
Thnkyou very much. I can browse to the DVDrom now in nautilus. The next step is how do I get Cedega to read it? I don't know why but Cedega doesn't want to even see it. When I click install, and tell it the path to the DVDrom:

/media/cdrom-1/Setup.exe

It says there is no such directory or file.

When you click browse, its like the DVD has no directories... or fiels or anything!!

Zeek  :cool:

---

### Post by Sukarn on 2006-10-28
shouldn't that be cdrom1 instead of cdrom-1 ?

---

### Post by Zeek00 on 2006-10-30
If you type

```
cd /media
ls -l
```

Notice what groups and users have permissions to the device. In my case I had the root user and group having read and execute rights to it. to solve the problem I asked my brother and we did this.

```
cd /dev
sudo -i
umount /dev/hdd
```

Upon returning to the /media folder we noticed that all other users besides root now had execute rights.

---

### Post by Zeek00 on 2006-10-30
> **Sukarn said:**
> shouldn't that be cdrom1 instead of cdrom-1 ?

No, it shouldn't be cdrom1, it is correctly stated as cdrom-1

---

