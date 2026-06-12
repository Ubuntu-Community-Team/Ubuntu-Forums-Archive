---
title: "Dual booting with linux as my main operator"
date: 2009-02-18
forum: General Help
---

### Post by stina123 on 2009-02-18
ok well i have some games for windows but wanted to play them on ubuntu so i would like to dual boot my computer with windows but i have an ubuntu laptop is there any way to install windows without first having to make windows as default? and also how would i go about starting this dual boot process?

---

### Post by blazemore on 2009-02-18
So you have a laptop with only Ubuntu on it at the moment?

It's difficult to dual-boot with Ubuntu installed first. Mainly because Windows overwrites Grub with its own bootloader, and you have to reinstall Grub.
But also, sometimes if there's another partition on there already, Windows doesn't name the system drive C, which can cause all kinds of installation issues.

I would:

1. Back up any data and/or settings (your entire /home directory, for example)
2. Booting from the LiveCD, delete every partition on your hard-disk, and then create one partition for the Windows installation, leaving the rest empty.
3. Install Windows to the new partition in the usual way.
4. Install Ubuntu, choosing the Guided - Use largests continuous free space option in the installer.

In a nutshell, install Windows first.

---

