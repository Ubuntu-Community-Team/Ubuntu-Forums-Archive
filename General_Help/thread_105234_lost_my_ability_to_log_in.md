---
title: "lost my ability to log in"
date: 2005-12-17
forum: General Help
---

### Post by tikal26 on 2005-12-17
hey as I reinstalled my hard drive I though everything was fine until now that I tried to log into my breezy partition and now I get an error sayignt that /dev/hda2/ where my breezy partiotn is is n not foudn but whehn I use a knopixx cd I can still acces it. any ideas?

---

### Post by aysiu on 2005-12-17
The error message appears when you try to log in?

You're at a graphical login, and when you type in your username and password, a warning box of some sort appears and says "/dev/hda2 cannot be found" and then you get the graphical login box again?

I just want to make sure I'm understanding what your problem is.

---

### Post by mlomker on 2005-12-18
[QUOTE=tikal26]hey as I reintsltted my hard drive I [/QUOTE]

I'm not sure what that word is.  Did you install another drive?  If you removed the drive and put it back exactly the same way then you should be fine, but if you added another drive then the partition numbering may have changed.

When the partition numbers change then you have to update **grub** before it will be able to boot again.

---

### Post by tikal26 on 2005-12-19
How do you update grub?
it used to be hdb2 but now is looking for hda2

---

### Post by mlomker on 2005-12-19
[QUOTE=tikal26]How do you update grub?
it used to be hdb2 but now is looking for hda2[/QUOTE]

I'd recommend using a Knoppix boot CD.  There are a few ways to accomplish it, but [this has worked for me.]("http://geodsoft.com/howto/dualboot/grub.htm#install")

---

