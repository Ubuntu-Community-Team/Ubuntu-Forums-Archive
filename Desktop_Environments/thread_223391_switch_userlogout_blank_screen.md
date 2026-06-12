---
title: "switch user/logout blank screen"
date: 2006-07-26
forum: Desktop Environments
---

### Post by yib on 2006-07-26
hi everyone,

Been having this same problem lately. sometimes (30% or 40% of the time) switching users in dapper freezes the computer with a blank screen. This has also happened, but less often when I log out. I have dapper installed on a centrino laptop using ati radeon 9600. I've read in other threads about possible problems with certain radeon graphic cards, but haven't seen any definite causes or solutions. Any help would be appreciated.

yib

---

### Post by Ziox on 2006-07-26
my guess is probably tweak your xorg.conf file, and try another driver for the radeon card...

---

### Post by yib on 2006-07-26
I dont' know what there is to do in xorg.conf to help the situation. As far as I know, all settings are correct, the only thing to do is change fglrx back to ati. Similar issues were present in breezy with ati drivers. I remember I wasn't able to come out of hibernate with graphic driver working. Back then I just settled with not using hibernate... I guess I could just not use switch users, but would be nice if that wasn't a problem. Thanks again.

Yib

---

### Post by Ziox on 2006-07-26
i'm not sure if it makes a difference, but maybe change "ati" to "radeon"...

---

