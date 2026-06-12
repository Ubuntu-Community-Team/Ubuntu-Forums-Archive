---
title: "Lucid 10.04 netbook, stuck at keyring, no keyboard, poulsbo install"
date: 2011-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jon_J on 2011-07-06
Hi,
I have a Dell Mini-10 with GMA500 poulsbo chip.
I installed ubuntu using "ubuntu-10.04-netbook-i386.iso"
I went to this page, [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
and installed the Emgd drivers, using this command:```

wget dl.dropbox.com/u/1338581/gma500/emgd-lucid.sh && sh ./emgd-lucid.sh 
```

Upon reboot I got to the desktop and my password was required in keyring.
I have no keyboard or mouse response at this point.
I can only back out by hitting my power switch to shut down.
I tried recovery selection in grub, but the low resolution graphics mode doesn't work either.
The above install must have modified xorg to the point that low-res graphics is unavailable.

Thank you for any suggestions. 
I have this netbook setup as multiboot, and if needed, 
I can modify files in Lucid from my earlier xubuntu on another partition.

---

