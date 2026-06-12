---
title: "reconfigure grub"
date: 2009-03-05
forum: General Help
---

### Post by Andreas1 on 2009-03-05
hello,
this might be obvious but i didn't find it anywhere on the forums yet:

i installed grub along with ubuntu

then i installed grub along with another distro on another partition, both distros were in the grub menu stored on the other partition, all fine

but since ubuntu is my main working environment and other partitions are supposed to be "playground" i wanted grub back on ubuntu and ran "grub-install hd0" in ubuntu. this restored my previous grub menu without the new distro.

so my question: how can i make grub "scan" for all operating systems, like when installing it along with ubuntu the first time? "grub-install" apparently used the old menu.lst that was already there before.

---

### Post by taurus on 2009-03-05
You can edit /boot/grub/menu.lst by hand and add an entry for the other distro.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Andreas1 on 2009-03-05
thank you

i did what you said, copied the new entries from playground/boot/grub/menu.lst  to  ubuntu/boot/grub/menu.lst, all work fine.

two questions though, more out of curiosity:

-do automatic changes to menu.lst (kernel updates) interfere with manual entries? and what if the kernel of the playground distro was updated?

-is there a way to "scan" for operating systems and reinstall/reset grub accordingly? how does it work when you install a distro? does is append the previous grub configuration found on a partition to the new one or does it find operating systems themselves, like with windows?

---

### Post by xtremo on 2009-07-10
Many thanks!

---

