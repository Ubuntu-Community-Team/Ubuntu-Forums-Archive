---
title: "X server fails to start"
date: 2007-03-22
forum: Desktop Environments
---

### Post by alex77 on 2007-03-22
Hi all,

I am trying to get ubuntu edgy working on my system. I have installed it using the alternative cd, but when i try to boot for the first time, it fails at trying to load the x server.

I get an error message telling me that it Failed to start the x server.

I have already tried booting with xforcevesa on, to no avail.

I am using an ati x1600 card, and I also have a widescreen monitor- would this cause problems?

Please Help!

Thanks

---

### Post by JoxBG on 2007-03-22
You're probably missing xorg.conf, which is generally not created on cmd-line or server install. Make one:

code : sudo Xorg -configure

Follow the steps, then try startx again.

---

### Post by alex77 on 2007-03-23
Sorted. Needed to fiddle about with xorg.conf, it didnt like the fact i have two graphics cards plugged in.

Thanks

---

