---
title: "Xubuntu desktop is black with icons but no wallpaper"
date: 2017-08-15
forum: Desktop Environments
---

### Post by twgray on 2017-08-15
After a new installation of Xubuntu 16.04 LTS, I experienced a faulty sata controller.  I repaired that and recovered the drive, just my home, opt and var directories were affected.  

Now,  the xfdesktop is just black.  All icons are still there but no wallpaper will display.  I've tried changing wallpaper from the right click Desktop Settings and from the main settings menu to no avail.  I've reinstalled, from synaptic, Xubuntu-desktop, xfdesktop, and lightdm...all to no avail.  None of the error logs show anything.  I think it has to be a corrupted configuration file but I can't find which one.

Any help is appreciated.

---

### Post by #&amp;thj^% on 2017-08-15
Try open a terminal and enter this:
```
xfdesktop & 
```

---

### Post by twgray on 2017-08-15
Thanks for the reply but this has no effect!

---

### Post by #&amp;thj^% on 2017-08-15
The only place to check maybe is in ~..cache/sessions/

---

### Post by Autodave on 2017-08-15
Have you tried putting one of your own pics on the desktop for wallpaper? Just right click on the image and tell it to "set as wallpaper".

---

### Post by twgray on 2017-08-15
Autodave, that was the key...apparently any .jpg NOT in my local Pictures folder will display...must be a permissions thing.  I'll dig deeper, but thanks to everyone who replied.  This has been an agravation for a while.

---

