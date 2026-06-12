---
title: "show boot text messages durung the startup"
date: 2011-07-16
forum: Desktop Environments
---

### Post by cccc on 2011-07-16
Hi

Howto configure Ubuntu 11.4 with Gnome to show boot text messages on the screen, each time during the startup?

---

### Post by Krytarik on 2011-07-16
1. Open the file "/etc/default/grub" for editing:
```
gksudo gedit /etc/default/grub
```2. Remove the parameters "quiet" and "splash" from the line "GRUB_CMDLINE_LINUX_DEFAULT".

3. Save / quit.

4. Update Grub:
```
sudo update-grub
```You may also want to have a look at this guide, for further reference:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Greetings.

---

### Post by cccc on 2011-07-17
Thx a lot, but what about noplymouth option:```
 GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```

---

### Post by Krytarik on 2011-07-17
> **cccc said:**
> Thx a lot, but what about noplymouth option:```
 GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```
Honestly, I didn't hear about those parameter until now, neither do I know if this works. But removing the parameters as stated previously should definitely work.

---

