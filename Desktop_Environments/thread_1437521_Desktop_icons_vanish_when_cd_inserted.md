---
title: "Desktop icons vanish when cd inserted"
date: 2010-03-24
forum: Desktop Environments
---

### Post by parth.s on 2010-03-24
Hey guys im using Ubuntu 9.04 and having this wierd problem recently.Whenever i insert the ubuntu 9.10 i386 cd to upgrade...the desktop icons dissappear and the right clicking ability also is gone.
I cannot access any of my drives through PLACES>Removable media
Hence i am unable to upgrade.Plz help.

---

### Post by parth.s on 2010-03-24
This is happening everytime i insert a cd in my cd rom.If i try to run "Nautilus &" it gives an error like "[1] 4763"

if i remove the media and then try Nautilus & this i what happens


parth@parth-desktop:~$ nautilus &
[1] 3779
parth@parth-desktop:~$ 
** (nautilus:3779): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

parth@parth-desktop:~$ 


and the icons are back and so is nautilus

---

### Post by NightwishFan on 2010-03-24
It seems nautilus is crashing. Perhaps you should file a bug report. Did it always do this or did the behavior start after a period of time?

---

### Post by parth.s on 2010-03-24
It has just started recently.Though i had recently modified the fstab file using the "gksu gedit /etc/fstab"  so that all the drives are mounted on startup.

---

### Post by NightwishFan on 2010-03-24
Ah, the plot emerges. Did you create a backup of the fstab before you edited? That might fix it. If not, try this:
```
gconftool-2 --recursive-unset /apps/nautilus
```

Then log out and log in.

---

### Post by parth.s on 2010-03-25
No i didnt take any backup of the fstab file...
I tried the command but only the desktop icons got restored...the problem still remains

---

### Post by NightwishFan on 2010-03-25
My advise to you is to backup your data and package cache and reinstall, or fix your fstab, as that might be the problem. The package cache is located in /var/cache/apt/archives after you reinstall, copy all the deb files from there back into the new cache, and you will not have to download all the updates you installed.

---

### Post by parth.s on 2010-03-27
Ok that would be my last resort...but the thing is that even after the icons disappear i can access the partitions and cd through run appln>run with file...or using any other software

also if i am reinstalling should i go for 9.10 or wait for lucid
thanks

---

### Post by NightwishFan on 2010-03-27
The beta is pretty stable but I recommend 9.10 right now to avoid all the Plymouth issues.

---

### Post by parth.s on 2010-03-27
I have the ubuntu 9.10i386 iso burnt on a cd and i am facing the same problem whenever i either mount the cd or the image(using gmount)..how do i manually update using synaptic manager as the autorun is not starting

---

### Post by NightwishFan on 2010-03-27
Update to 10.04 or 9.10? For 9.10 from 9.04 is here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

