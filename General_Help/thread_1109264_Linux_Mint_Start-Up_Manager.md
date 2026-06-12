---
title: "Linux Mint Start-Up Manager"
date: 2009-03-28
forum: General Help
---

### Post by ninjapirate89 on 2009-03-28
I installed startup-manager in Linux Mint so I could change the time the boot menu is displayed but when I went to change it, I didn't find the option as I did when I used ubuntu. Any ideas?

---

### Post by linuxisevolution on 2009-03-28
> **ninjapirate89 said:**
> I installed startup-manager in Linux Mint so I could change the time the boot menu is displayed but when I went to change it, I didn't find the option as I did when I used ubuntu. Any ideas?

Are you using the Grub boot manager?

---

### Post by Chemical Imbalance on 2009-03-28
```
gksudo gedit /boot/grub/menu.lst
```

then edit this with whatever timeout you want:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

---

### Post by ninjapirate89 on 2009-03-28
> **Chemical Imbalance said:**
> ```
gksudo gedit /boot/grub/menu.lst
```

then edit this with whatever timeout you want:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

Thank you that did just what I wanted.

---

