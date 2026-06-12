---
title: "Dual Boot problems"
date: 2009-04-01
forum: General Help
---

### Post by big daddy zane on 2009-04-01
:???:I installed Ubuntu on a separate hard drive along with xp pro. I tried to install wine to access my xp apps. I started having problems so I uninstalled wine. I cannot boot to xp pro. When I restart it automatically boots to Ubuntu (8.10). It flashes the boot option screen but you cannot change anything. Additionally, I cannot change any options if I try to use the install disk for Ubuntu. Can anyone help. I am a Linux noob. Please explain in laymen's terms.

---

### Post by SubNetMask on 2009-04-01
> **big daddy zane said:**
> :???:I installed Ubuntu on a separate hard drive along with xp pro. I tried to install wine to access my xp apps. I started having problems so I uninstalled wine. I cannot boot to xp pro. When I restart it automatically boots to Ubuntu (8.10). It flashes the boot option screen but you cannot change anything. Additionally, I cannot change any options if I try to use the install disk for Ubuntu. Can anyone help. I am a Linux noob. Please explain in laymen's terms.

Even if you install on a separate Hard Drive, it will overwrite the windows MBR, so you can't boot from windows anymore, Windows MBR does not go well with other OS'es, use grub to set windows XP up as a bootable OS.

---

### Post by zvacet on 2009-04-01
Go to the **applications>accessories>terminal** and there  type 

```
sudo fdisk -l
```

and post output here.

---

