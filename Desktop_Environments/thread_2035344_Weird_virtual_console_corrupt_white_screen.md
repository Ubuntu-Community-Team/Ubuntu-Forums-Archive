---
title: "Weird virtual console: corrupt white screen"
date: 2012-07-30
forum: Desktop Environments
---

### Post by nikonian on 2012-07-30
Hi guys, these are my specs:

Asus P5LD2-VM/S mobo (Viglen OEM version, denoted by the suffix "S")

Nvidia GeForce 6200

Ubuntu 12.04 64 bit using "version-current" binary Nvidia drivers


System is running fine using Gnome Shell, but when I attempt a virtual console using CTRL+ALT+F1, I get a white screen with garbled black text on it, and black lines at the bottom of the screen. 

Oddly, last night I did a fresh install, then added:

```
sudo apt-get update && sudo apt-get dist-upgrade
``` 

(didn't reboot after this) and it didn't have this white screen error, whilst the system was up. Today it has reverted to doing this again. 

Any idea what could be wrong? Thanks

---

### Post by albandy on 2012-07-30
Disable splash in boot and test if works correctly.

---

### Post by nikonian on 2012-07-30
> **albandy said:**
> Disable splash in boot and test if works correctly.

It's alright, I have fixed it by putting:

```
GRUB_GFXMODE=1024x768
```

in ```
/etc/default/grub

```

and then running ```
sudo update-grub
```

Thank you :)

---

