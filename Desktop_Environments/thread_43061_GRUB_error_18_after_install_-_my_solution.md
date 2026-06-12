---
title: "GRUB error 18 after install - my solution"
date: 2005-06-20
forum: Desktop Environments
---

### Post by holr on 2005-06-20
Hi folks,
   New to kubuntu but have messed with ubuntu a little in the past. I has a funny problem today, i.e. after installing kubuntu (dual booting with windows xp) it kept coming up with a boot error from GRUB, code 18. I knew I had it working on a prior install, so decided to tinker....

...i managed to get rid of this problem by NOT doing the autoconfigure partition in the setup. I dont have any screenies to hand, but imagine that you already have a working winxp partition, and a bunch of free space. When I selected the free space and did autopartition it created a swap and a '/'. However, the '/' was listed as "primary" rather than logical. The swap was logical, (and of course, my untouched winxp was primary).

I changed it to read thus:
windows xp was primary (i.e. didnt touch it)
swap: logical
'/': logical (instead of primary)

This now meant grub worked again for me!

btw I checked the forums and a lot of posts I found regarding this issue seemed to involve going into the bios etc. I just thought Id give my 2 cents worth as I have had sooo much help from this forum in the past ;-) Hope someone can find this useful.

---

### Post by foxmulder on 2006-06-26
Hm, have the same problem: an old P3 866mHz with a 250gb harddisk and XP on the first partition: hope this fixes my problem!

---

### Post by rocknrolf77 on 2006-07-05
Thank's for this. Had no idea what was happening and this solved my problem.

---

### Post by bioShark on 2008-03-15
Hi

I know it's a while since you wrote this post, but thanks anyway for it, because it solved my problem. I had exactly the same problem as you.

Thx

---

