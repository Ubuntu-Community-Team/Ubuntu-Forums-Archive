---
title: "can't stay logged in to kde"
date: 2009-10-11
forum: Desktop Environments
---

### Post by bzarnsy on 2009-10-11
i'm running karmic and primarily use gnome but i also have kde, xfce, and
e17. i'm in gnome and want to use kde so i hit logout, the logout dialog pops up, i hit logout the screen goes dark then i get the boot splash for a
couple seconds then the kde splash fades in, then i see the gnome desktop
with the logout dialog for about a second then the kde desktop appears.
now i'm in kde but when i click the menu button or any where else the screen goes blank and the i'm right back at the gdm log in screen.
what's up with that?

---

### Post by Zorael on 2009-10-11
I don't know where to begin. Intel graphics? KDM or GDM?

There's a bug that causes X to segfault when you log out when using intel graphics. kdm tries to reuse (regenerate) the X session instead of completely shutting it down and starting a new one, but crashes. I'm not sure if gdm does this per default. 

Perhaps fixing that may stop whatever's causing the rest from happening? It's fixed upstream in new drivers, such as the ones in Karmic's repos, but you can work around the issue by telling your login manager (kdm/gdm) to terminate the server and starting a new one instead of regenerating the old one. For kdm, you need to find the line **TerminateServer** in **/etc/kde4/kdm/kdmrc** and set it to uncommented and **true**. For gdm, I don't know.

If you're not on intel graphics, pass.

---

### Post by bzarnsy on 2009-10-11
i'm sorry. not enough info.
dell dimension 4700  p4 3.2 gig
2.5 gig ddr2
ati x1300 pro video
using gdm

---

### Post by VanHammersly on 2009-10-13
I'm facing the same problem on my MacBook Pro 1,1.  Ati x1600.

---

### Post by bzarnsy on 2009-10-16
evidently recent updates solved this problem.

---

