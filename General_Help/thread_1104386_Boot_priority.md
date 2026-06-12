---
title: "Boot priority"
date: 2009-03-23
forum: General Help
---

### Post by invincibletoviruses on 2009-03-23
i was wondering if i can switch the position of operating systems on the grub menu. I use Xp pro more often than ubuntu and would like it first on the menu so it will automatically boot.

---

### Post by mocoloco on 2009-03-23
Yes. The file you want to edit is /boot/grub/menu.lst.  You must edit this as root.
Hit Alt-F2, then type in
```
gksu gedit /boot/grub/menu.lst
```

Just scroll down near the bottom, after the line "## ## End Default Options ##".   You'll see each boot option starts with a "title".  Find the one for XP, cut out that section and paste it as the first option.  You can also remove or comment out any lines about "other operating systems" because you won't need them anymore.

Also note, in the file it tells you how to change which line is the default option to boot from.  I recommend against using this, because when you update the kernel there are new lines added.  It's easiest to leave the default of the top line and move XP to the top.

Gedit automatically creates a backup of the last version of the file so if you mess anything up you can go back to it.

---

### Post by drs305 on 2009-03-23
To accomplish the same thing without having to manually edit menu.lst you can install and run Startup-manager. It's a gui app that will allow you to select the default OS as well as set menu timeouts and much more. 

See the link in my signature line to a guide for installing and running StartUp-Manager. It also has some tips for manually editing menu.lst

---

### Post by invincibletoviruses on 2009-03-23
Solved thanks!

---

