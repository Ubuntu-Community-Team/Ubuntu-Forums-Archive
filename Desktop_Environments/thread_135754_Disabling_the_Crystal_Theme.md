---
title: "Disabling the Crystal Theme"
date: 2006-02-24
forum: Desktop Environments
---

### Post by tadashi on 2006-02-24
Is there  a way to disable this theme?  Or unistall it?  I really like it but I think it is too resource intensive for my little laptop. :(

I assume you cannot just delete the directory and there is no mention of it in any package manager.  Is there a make uninstall command?

---

### Post by Xian on 2006-02-24
You disable themes in the KDE Control Center.
Pick one that is less resource hungry.

---

### Post by Freddy on 2006-02-24
If you really want to remove it and you have compiled it yourself, just use your konsole and place yourself in the sourcedir and write:
```
sudo make uninstall
```
If you have used apt-get for the install just use:
```
sudo dpkg -r "packagename"
```
/// Freddan

---

### Post by tadashi on 2006-02-24
Nope make uninstall said no directions (or something like that).  <sigh>  Time to reinstall for the 8th time. hehehe  Learning curve is high. =D

---

### Post by Freddy on 2006-02-25
You need to place yourself inside the unpacked source.   /// Freddan

---

### Post by tadashi on 2006-02-25
I was in the source directory. I never deleted it.  Speaking of which after I compile something can I delete the directory?  I was not sure so have left them all.

---

