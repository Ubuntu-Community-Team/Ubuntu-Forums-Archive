---
title: "too many files"
date: 2007-07-24
forum: Debian
---

### Post by COLiNx86 on 2007-07-24
lately i've been trying to get linux installed first i tryed ubuntu but couldn't get it to work and then i tryed xandros but am not really a fan and i'm about to try ubuntu agian but i really want debian 4.0 there's just way to many files. no way am i going to download 21 iso's for an operating system. is there any easier way with like one cd or dvd?

---

### Post by tbroderick on 2007-07-24
If you are connected to the internet, you can use the [net-installer]("http://www.us.debian.org/CD/netinst/"). Only 184 MB. Or just download the first CD. The other 20 are not needed to install. They are just full of all the stuff from the repos.

---

### Post by CREEPING DEATH on 2007-07-25
You only need the first CD or the net installer, the rest are fairly useless.

CD

---

### Post by Bachstelze on 2007-07-25
> **CREEPING DEATH said:**
> You only need the first CD or the net installer, the rest are fairly useless.

...unless you do not have an Internet connection, in which case it is very useful to have 21 CDs full of apt-get'able packages.

---

### Post by Pobega on 2007-07-25
> **HymnToLife said:**
> ...unless you do not have an Internet connection, in which case it is very useful to have 21 CDs full of apt-get'able packages.

Even *if* you don't have an active internet connection, you really don't need all 21 CDs. The first few should suffice, seeing as the ISOs are created by using the results from popcon (The Debian package popularity contest), so the most popular (And required) packages make it to disc one, most popular but not required make it to disc two, and the less popular packages make it to disc 3, and so on so forth.

But as long as you have an internet connection at installation time you should be fine; The only problem would be if your ethernet doesn't seem to be supported by the net-installer (This IS possible, since from what I understand some are still proprietary).

---

