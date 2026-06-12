---
title: "USB plugs dont'n work any longer"
date: 2008-12-16
forum: General Help
---

### Post by Jayhawker on 2008-12-16
Please, suddenly, usb plugs in my computer don't detect any memory stick inserted in. Has Linux any way to solve it, provided it's a software problem?

Thanks a lot.

---

### Post by northern lights on 2008-12-16
Please connect the device and subsequently post the output of ```
lsusb
```

Are either the uhci-hcd or ehci-hcd modules loaded?

If that sounds like gibberish to you, check in "/lib/modules/2.6.27-9-generic/kernel/drivers/usb/host/" (replace kernel version by your current version). Or run ```
locate ehci-hcd
```

If not, you should be able to load it via```
sudo modprobe ehci-hcd
```

---

