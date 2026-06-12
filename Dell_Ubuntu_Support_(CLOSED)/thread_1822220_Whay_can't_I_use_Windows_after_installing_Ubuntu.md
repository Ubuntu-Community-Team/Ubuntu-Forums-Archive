---
title: "Whay can't I use Windows after installing Ubuntu?"
date: 2011-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by king123440 on 2011-08-10
**I'm sure when it asks to delete Windows XP and install Ubuntu or keep Windows XP and continue install Ubuntu i chose one. But after installing Ubuntu I just can't access Windows XP. Can anybody tell me why?**

---

### Post by Basher101 on 2011-08-10
You chose ***one***. Exaclty which one? The delete xp? Otherwise do you see grub on bootup (purple background) ? Sounds like a bootloader issue (if you did not delete xp)

---

### Post by zeroseven0183 on 2011-08-10
Does it go directly to Ubuntu during boot up? If it does, try to press and hold SHIFT to see the grub menu and from there select Windows. This is assuming that when you installed Ubuntu, Windows was not erased.

---

### Post by ZaphodFJ on 2011-08-10
If you keep booting into Ubuntu and cannot find any bootloader, make sure Windows is still there (to reassure yourself, and to get the correct help).

Under 'Places' (assuming you are using Gnome as your UI), or in the side-panel of Nautilus you will hopefully see your hard disk and your Windows partition.  Double-click on it, hopefully you will see folders that look like the top-level contents of C: "Windows", "Program Files", etc.

If you can see that, then it's a bootloader problem.

If you cannot see that, then you have accidentally killed Windows.  I found this out the hard way once!

Post an update to get help on sorting out your bootloader.  The more detail you can give, the better the help you will get.

---

