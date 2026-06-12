---
title: "Boot splash garbage"
date: 2010-08-26
forum: Desktop Environments
---

### Post by tigerendk on 2010-08-26
Under boot I often get's this screen (see attachment) instead of the ubuntu boot splash.

It's Lucid running on a Lenovo T410i laptop, with nvidia graphics adaptor.

Where to start debugging? ;)

---

### Post by xdemo on 2010-08-26
Wow that looks pretty strange. Does the system still boot though?

Try modifying the GRUB_GFXMODE entry in */etc/default/grub* with an appropriate resolution for your computer.

Then;
```
$ sudo update-grub
```and reboot

If that doesn't work you could also try changing:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
for
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=792"
```

---

