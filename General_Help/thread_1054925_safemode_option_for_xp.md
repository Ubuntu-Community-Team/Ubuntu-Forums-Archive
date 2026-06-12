---
title: "safemode option for xp"
date: 2009-01-30
forum: General Help
---

### Post by Milkman08 on 2009-01-30
Hi Linux users around the world!
I'm a newbie and I love to learn Linux in this amazing world of open source softwares.
My problem is that now that I installed hardy haron and grub boot screen is installed, I cant boot win xp in options like safemode and ... that previous boot screen provided to me.
What should I do now?
Thanks

---

### Post by hyper_ch on 2009-01-30
boot ubuntu, run the following commands, post teh output here:
```

sudo fdisk -l

```
```

cat /boot/grub/menu.lst

```

---

### Post by blazemore on 2009-01-30
It helps to understand the boot process.

GRUB boots Linux directly.
However, Grub doesn't boot Windows directly.
Instead, it passes control over to the Windows bootloader, which doesn't know or care that it hasn't been booted first.

So after you choose the Windows XP option, you should hammer F8 )or whatever it is) and that will bring up the options for the Windows bootloader.

---

### Post by khedron on 2009-01-30
On Windows you normally can get onto the Safe Mode selection menu by pressing F8 when Windows just starts to boot. So:

1. Start up the computer.
2. Select Windows in the GRUB menu.
3. Press return and then quickly start pressing F8 many times.

This should get you onto the Windows boot options menu, where you can choose safe mode etc.

*Edit: beaten... this has happened to me before...*

---

### Post by Milkman08 on 2009-01-30
Thanks guys! :) You've been a real help.

---

