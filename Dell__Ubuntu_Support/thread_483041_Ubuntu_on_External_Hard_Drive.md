---
title: "Ubuntu on External Hard Drive"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by brk1125 on 2007-06-24
I tried to install Ubuntu onto my external hard drive and it ended up wiping my entire hard drive out on my computer. What did I do wrong?

---

### Post by ESPOiG on 2007-06-24
you selected the wrong hdd to install it to

when you are in the installer it will say auto, largest free space or manual, you probaly want manual, when in this you find which one is your external hdd, then you partition it as so

1. as ext3 and mount point as /
2. as swap
if you want seperate /home then just make a third partition and mount point as /home

also i dunno but you will probaly have to install grub (boot loader) to it for it to be able to boot but i dunno depends on how you want it to set up

---

### Post by Tethtibis on 2007-06-26
i have yet to get ubuntu working on an external drive. it will install, but never boots right, and yeah, i turned it on in bios. :OP

---

