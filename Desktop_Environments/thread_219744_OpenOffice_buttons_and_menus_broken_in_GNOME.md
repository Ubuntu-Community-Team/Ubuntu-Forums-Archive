---
title: "OpenOffice buttons and menus broken in GNOME"
date: 2006-07-20
forum: Desktop Environments
---

### Post by nekr0z on 2006-07-20
I'm moving from KDE to GNOME, and have some problems with it. One of them is: the menus and buttons in OpenOffice.org are blank until I hover my mouse over them. This only happens in GNOME, and when I boot back to KDE everything is allright.

What can be the matter (and the workaround)?

---

### Post by ThrobbingBrain66 on 2006-07-20
try installing openoffice.org-gnome and openoffice.org-gtk

i think this will solve your problem.

---

### Post by annda on 2006-07-20
i've been having the same problem for some time now. i don't know exactly after which update it happened because i use GNOME and XFCE desktops interchangeably so i missed this 'crash'. i assumed it would go away with next updates (as so many bugs do), but not in this case - and there was an oo2 update in the meantime.

i do have both packages ThrobbingBrain66 suggested already installed, but the problem seems to lie somewhere else.

anybody has any ideas? does anyone have that strange behavior too? if so, maybe we could narrow it down.

---

### Post by nekr0z on 2006-07-20
I moved to GNOME by installing ubuntu-desktop package, which means both of these packages were installed, too. I double checked it now, the packages are here. And so is the problem.

---

### Post by nekr0z on 2006-07-20
Damn, I should have checked Launchpad! [Here]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/41831") is the solution: go to console and do ```
rm -Rf ~/.gtk*
```
And everything works as a dream, Devil knows why...

---

### Post by TeKKi on 2006-07-21
thankyou nekroz!! :)

---

### Post by eriqthegeek on 2006-08-01
Thank you, thank you, thank you!

I was having the same problem.  In my case, I believe it was brought on by experimenting with switching from Gnome to kubuntu this past weekend.  I ended up switching back, and after doing so was having the same button/menu problem.  Removing the .gtk* stuff fixed it for me too.  :)

---

