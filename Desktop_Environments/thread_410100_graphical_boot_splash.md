---
title: "graphical boot splash"
date: 2007-04-15
forum: Desktop Environments
---

### Post by infinitezero on 2007-04-15
Is there a way to get rid of the graphical boot splash?

Thanks,
iz

---

### Post by taurus on 2007-04-15
Remove either **quiet** or **quiet splash** from the kernel entry in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ardchoille42 on 2007-04-15
Remove the "splash" from your kernel lines in /boot/grub/menu.lst. You can also remove "quiet" but that will show tons of stuff.. I found that quite annoying.

---

### Post by infinitezero on 2007-04-16
Cool, I appreciate the info.


Thanks,
iz

---

### Post by javaJake on 2007-04-17
I believe (not sure) that if you remove the quiet, but not splash, the splash screen will list out what it is doing like in Dapper.

---

