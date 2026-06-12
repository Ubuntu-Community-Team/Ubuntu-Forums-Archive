---
title: "Grub loader doesn't work, can't get into any OS"
date: 2009-05-24
forum: General Help
---

### Post by Marty McFly on 2009-05-24
I have grub 1.5 on my desktop to dual boot xp/ubuntu.  I haven't booted up this box in about a month or so, but now when you start it it says grub loader 1.5 starting then just gives me a command prompt:

grub>

I don't know what to do to get either OS to load.  I hit 'help' to see the available commands but couldn't figure it out.  Any advice?

Thanks.

---

### Post by hjacker on 2009-05-24
You should perhaps boot from "Super GRUB bootcd" and alter the settings.

---

### Post by VMC on 2009-05-24
> **Marty McFly said:**
> I have grub 1.5 on my desktop to dual boot xp/ubuntu.  I haven't booted up this box in about a month or so, but now when you start it it says grub loader 1.5 starting then just gives me a command prompt:

grub>

I don't know what to do to get either OS to load.  I hit 'help' to see the available commands but couldn't figure it out.  Any advice?

Thanks.

from that grub prompt type the following:
```
find /boot/grub/stage1
```

then use the output of that and see if you can restart your menu:
```
configfile (hd0,2)/boot/grub/menu.lst
```

[The (hd0,2) is just example. Use your output]

---

