---
title: "GRUB questions"
date: 2006-04-15
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-15
Hey everyone. I installed Ubuntu on my PC (finally) and the installation was easy. Partitioning was hard and I don't know what I did but it seems to work. I made my PC dual-boot. Anyway, when the computer boots up it has the list of OS's and down the bottom it says: Windows NT/2000/XP (loader). And it's meant to say Windows XP. What happened? (P.S. I haven't tried booting into the Windows NT/2000/XP (loader) thing yet)

---

### Post by paddyg on 2006-04-15
Nothing. Grub is just going to hand boot to the win loader there. If you don't like that title, just edit the title line for windows in /boot/grub/menu.lst

---

### Post by Mr Egg on 2006-04-15
Okay, thanks alot paddyg. I'll try booting into it next time I turn on the computer :).

---

