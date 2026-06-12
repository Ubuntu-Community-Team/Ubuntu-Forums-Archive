---
title: "I screw it, please, help!"
date: 2008-11-12
forum: Desktop Environments
---

### Post by fabrile on 2008-11-12
Hi I installed Ubuntu 8.10
Everything OK, so i wanted "THE CUBE"
y had to install KDE and well i've done it.
After a few days i wanted to disable all that visual stuff.
So I DISABLED THE KDE wherever it is, and i got A BLANK SCREEN!
i re booted but i only have the sistem line.

I SCREW IT!!!   how do i get the menus, the images, all the stuff...

PLEASE, HELP ME

---

### Post by crazyness003 on 2008-11-12
You didnt have to install KDE to get the desktop cube. Thats enabled in composition. Ubuntu uses compiz-fusion to do that.
As for tanking KDE, it seems as if you installed the KDM (KDE Desktop Manager) and after removing it, now are left with nothing.
If you wanna get your gnome Ubuntu back, try typing this in the command prompt
```
sudo apt-get install ubuntu-desktop
```(remember that sudo is a dangerous command to issue, so be careful when you do isue it)
Basically what you're trying to do is restore the default Ubuntu Desktop (gnome, ubuntu-themes, ubuntu-sounds, etc).
Hopefully that works. It should also install GDM (Gnome Desktop Manager).
All GDM/KDM does is give you a 'login screen' to your particular desktop manager. When you install KDE, you probably removed the GDM (and gnome altogether). Then when you removed KDE, you were left with no DM.
So, i presume (and hope) that by reinstalling Gnome, you should be fine.

Give us an update on what you do and if it works

---

### Post by fabrile on 2008-11-12
Well, I've done that but it said thati it is in the most recent version.
NO CHANGE...

---

### Post by crazyness003 on 2008-11-12
> **fabrile said:**
> Well, I've done that but it said thati it is in the most recent version.
NO CHANGE...

Ok, onto another approach.
You may need to star up your GDM.
Thry this
```
sudo /etc/init.d/gdm start
```

---

### Post by fabrile on 2008-11-12
> **crazyness003 said:**
> Ok, onto another approach.
You may need to star up your GDM.
Thry this
```
sudo /etc/init.d/gdm start
```

The answer is Not Starting GNOME Display Manager; it is not the default display manager

---

### Post by crazyness003 on 2008-11-12
OKay, try this (got it from here [http://ubuntuforums.org/showthread.php?t=674776](http://ubuntuforums.org/showthread.php?t=674776))
>                                   **Re: how  set gdm as default**             
                                                                That only makes the GNOME session the default *session*. In order to make GDM the default *display manager*, try running:

     Code:
    ```
 dpkg-reconfigure gdm 
```It should ask you whether you want GDM to be the default display manager or not.


EDIT: Also check this out:
[http://ph.ubuntuforums.com/showthread.php?t=887735](http://ph.ubuntuforums.com/showthread.php?t=887735)

---

### Post by iKonaK on 2008-11-12
Try selecting from grub options the recovery mode and change from there.

---

