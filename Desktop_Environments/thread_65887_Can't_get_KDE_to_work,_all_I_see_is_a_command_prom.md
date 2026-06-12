---
title: "Can't get KDE to work, all I see is a command prompt. HELP!"
date: 2005-09-15
forum: Desktop Environments
---

### Post by romnation on 2005-09-15
I just loaded the live cd, and after everything, I just get a Ubumtu@Ubuntu command prompt. How do I get to KDE? Do I HAVE to be connected to the internet when doing it, maybe?

---

### Post by zAo on 2005-09-15
You dont have to be connected to the net.
Please post /var/log/Xorg.0.log by typing
```
more /var/log/Xorg.0.log
``` 
If you want to save it, and post it from windows
```
cat /var/log/Xorg.0.log > /windowsD
``` 
Assuming that /windowsD a FAT32 disk is!

---

### Post by romnation on 2005-09-15
No, its NTFS

---

### Post by romnation on 2005-09-15
KDE is preloaded on the cd right? BTW, its the live cd.

---

### Post by romnation on 2005-09-15
bump, please help

---

### Post by agm642 on 2005-09-15
If it's a normal Ubuntu Live CD, it doesn't include KDE.

---

### Post by jbinc1 on 2005-09-15
Try Kubuntu. It has the KDE gui.

---

### Post by Takis on 2005-09-17
Hello,

First a bit of advice with respect to forum etiquette: you don't need to bump your post 3 times in as many hours. It can be seen as annoying, and certainly won't help your problem (people will see that there are a couple of replies and may skip it). You should consider bumping after a day or so.

Anyway, let's see what we can do. I'm doubtful that whether you have the Kubuntu or Ubuntu live CD, it seems that X isn't able to start (or tries, then crashes). So you're at the command prompt, yeah? Try typing 'startx' and let us know what happens.

---

