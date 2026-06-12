---
title: "After ATI driver update followed by blank screen"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by irunwithknives on 2008-04-17
When I install the ATI restricted driver for my ATI 800 card, when I reboot, i get a blank black screen *after* GRUB screen.

I believe that to fix that, you must type Esc to reach the terminal thingy, then type

```
dpkg-reconfigure xserver-xorg
```

and set your system settings,
then when you are done with that, type

```
shutdown -r now
```

Just checking to make sure this is true so that it doesnt screw up my computer.

Thanks,
irunwithknives

---

