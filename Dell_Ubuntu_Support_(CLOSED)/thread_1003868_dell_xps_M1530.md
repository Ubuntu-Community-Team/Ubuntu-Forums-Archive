---
title: "dell xps M1530"
date: 2008-12-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manasmohan on 2008-12-06
my system's config is 3gb ram, 2 ghz, 250 gb hdd, nvidia geforce 8400 graphics card.... i have just installed the ubuntu 8.10... my system's touch pad is not working and i am not able to install the drivers of the graphics card.... please help me out... thanks..

---

### Post by Gausian on 2008-12-06
to fix your touchpad, do the following:

```
sudo gedit /boot/grub/menu.lst
```

add the following text to the end of the kernel line

```
i8042.nomux=1
```

---

