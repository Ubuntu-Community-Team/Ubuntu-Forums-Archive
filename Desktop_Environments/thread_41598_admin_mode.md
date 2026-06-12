---
title: "admin mode"
date: 2005-06-14
forum: Desktop Environments
---

### Post by wake-kitty on 2005-06-14
hi all i cant get my win modem to work so i decided to plug my kubuntu laptop to my windows network. when i tried to enter the administrator mode in network config, (control center) entered the correct password it wil show Loading then will just kick me back to the Konqueror screen. when its suppose to let me edit the config which was grayed out befor i enter the admin mode. any idea why this happens?

---

### Post by Xian on 2005-06-14
You can do a workaround by entering this in a terminal:

```
$ kdesu kcontrol
```

---

### Post by wake-kitty on 2005-06-14
wow! worked like a charm! thank you so much xian  :grin:

---

### Post by oakhilltop on 2005-06-14
So what's up with kubuntu.

Admin mode doesn't work for me either.

Kuser crashes.

Seems pretty unstable to me.

Also, if I use kdm I can shutdown from my logout screen in kde, but not gnome. If I use gdm, I can shutdown from my logout screen in gnome, but not kde. Arghh! LInux needs to get some compatibility.

---

### Post by wake-kitty on 2005-06-14
well im new with linux and kubuntu was the 1st distro i tried. i also noticed several crashes. and my kopete was acting a lil weird. cant get my win modem to work but its still a nice experince. im fron winxp so kde gives me the winxp feel. so im running a smooth migration to linux  :)

---

### Post by kubuntuuser on 2005-06-15
Updating to kde 3.4.1 will not fix this problem

See the kde3.4.1 changelog listed here

[http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php](http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php)

---

