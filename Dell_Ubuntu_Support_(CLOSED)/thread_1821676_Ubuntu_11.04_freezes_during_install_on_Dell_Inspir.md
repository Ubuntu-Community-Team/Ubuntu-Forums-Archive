---
title: "Ubuntu 11.04 freezes during install on Dell Inspiron N4010"
date: 2011-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trae329 on 2011-08-09
I decided to install Ubuntu 11.04 Natty Narwhal today dual-boot with my Windows 7 Home Premium on my Dell Inspiron 14R (Non-Switch Lid Version).

When getting to the end of the install of Ubuntu when done installing language packs, it freezes. I can't move the cursor or anything.

Using Wubi works, but I would rather want to dual-boot the 'Live CD' way.

Please help!

Thanks in advance,

Trae329

---

### Post by bcbc on 2011-08-09
Probably a bad burn on the CD then. I don't see why there should be a difference between running Wubi on it and a normal install.

When you boot from the CD, hit the spacebar when you see the keyboard icon, and from the extended menu, select "Check CD for defects"

PS this ppa fixes the Fn-F4/F5 brightness control assuming you're using the onboard intel gpu: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

---

### Post by cpbl on 2011-09-04
Installing 11.04 on a Dell Inspiron N4010 yesterday by USB (clean install, next to Windows 7), it crashed mid-way through the install. I submitted a bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/840692](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/840692)
and someone claims its related to an apt bug.
Indeed, the computer now boots into Ubuntu okay, but apt-get update is pretty broken...

---

### Post by bcbc on 2011-09-04
Try booting in recovery mode and then select "fix packaging errors".

---

