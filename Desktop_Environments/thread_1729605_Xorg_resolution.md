---
title: "Xorg resolution"
date: 2011-04-15
forum: Desktop Environments
---

### Post by Mosabama on 2011-04-15
I have ATI driver and everything works great on GUI mode.
but when I switch to tty1 or even while loading the resolution is really big.
each letter shows really big that the screen can only fit a small paragraph. how can I change this with out effecting the resolution of gdm cause I like it the way it is.

Thanks

---

### Post by Mosabama on 2011-04-15
I found the solution:

add this to /etc/default/grub file:

```
GRUB_GFXMODE=1024x600 #or whatever your VGA supports. 
GRUB_GFXPAYLOAD_LINUX=keep
```
then run:

```
sudo update-grub
```

---

