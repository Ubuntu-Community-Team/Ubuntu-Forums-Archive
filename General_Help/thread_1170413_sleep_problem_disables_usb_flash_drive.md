---
title: "sleep problem disables usb flash drive"
date: 2009-05-26
forum: General Help
---

### Post by shelbyvision on 2009-05-26
I didn't used to have this problem, and I think it started when I upgraded from gutsy to hardy. When I put my HP omnibook xe4400 laptop into suspend mode, and then wake it up, and then insert the usb thumb drive, or the usb external hard drive, nothing happens. As far as I can tell, these are the only things affected. If I plug in the usb printer after suspend, it works fine. If I want to use the flash drive or external hard drive, I have to re-boot, and then they work normally. This is very inconvenient! I researched this over the weekend, and found a few similar problems discussed, and tried some tweeks, but nothing has worked so far. Please help! 	](*,)

---

### Post by kmitnick on 2009-05-26
run this in terminal and post the output
```
ls /dev | grep sd
```

---

### Post by kerry_s on 2009-05-26
take out the usb before suspend.

press alt+f2
type> gksudo gedit /etc/pm/config.d/config
put:

SUSPEND_MODULES="usbcore"

---

### Post by shelbyvision on 2009-05-26
> **kmitnick said:**
> run this in terminal and post the output
```
ls /dev | grep sd
```

ptysd
ttysd

---

### Post by shelbyvision on 2009-05-26
> **kerry_s said:**
> take out the usb before suspend.

press alt+f2
type> gksudo gedit /etc/pm/config.d/config
put:

SUSPEND_MODULES="usbcore"

THANKS Kerry, that seems to have fixed it. So simple, but there's no way I would have ever figured it out. :D

---

