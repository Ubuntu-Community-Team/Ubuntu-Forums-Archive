---
title: "I removed entire grub and installed it again,  startupmnager won't work"
date: 2009-01-25
forum: General Help
---

### Post by Lukasz Tarkowski on 2009-01-25
I removed entire grub and installed it again,  startupmanager won't work.
Only usplash works
I did the following
```
sudo apt-get install grub

sudo grub

root (0,2)

setup (hd0)

And sudo apt-get install startupmanager


```

Any solutions?

---

### Post by zvacet on 2009-01-25
Try to reinstall grub [this]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") way.

---

### Post by Lukasz Tarkowski on 2009-01-25
I followed both instructions:(
It didn't work:-({|=

---

### Post by Lukasz Tarkowski on 2009-01-25
Here is my code

```
splashimage=(hd0,2)/boot/grub/splashimages/97900-StargateAtlantis.xpm.gz
```

---

### Post by zvacet on 2009-01-26
```
cat /boot/grub/menu.lst
```

and post it here

---

### Post by Lukasz Tarkowski on 2009-01-26
**I have formatted Ubuntu,  Its fine now.**
The problem is whenever I try to reinstall grub startupmanager stops working :(

---

### Post by Lukasz Tarkowski on 2009-02-04
I think the solution is update-initramfs -u.  I am not to sure , I am guessing that what it was! I formated Again and everything works fine

---

