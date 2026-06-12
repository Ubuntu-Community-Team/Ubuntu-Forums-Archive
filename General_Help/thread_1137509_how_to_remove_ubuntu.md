---
title: "how to remove ubuntu?"
date: 2009-04-25
forum: General Help
---

### Post by JakeHinojosa on 2009-04-25
no, im not going to remove ubuntu. i NEVER will. but i was just wondering, how does a person remove ubuntu off of their computer?

---

### Post by CatKiller on 2009-04-25
Well, you don't really uninstall an operating system, since a computer with no operating system is pretty useless. You replace that operating system with something else.

However, if you've got a dual-boot solution, so you've already got your other operating system installed, then you have a couple of options, depending on how you're dual-booting. If you've installed Ubuntu through Wubi then you can just uninstall Wubi the same as any other Windows application. If you've got separate partitions and GRUB as your bootloader then you remove the Ubuntu partitions and replace GRUB with Windows' own bootloader with *fixmbr* from Windows' Recovery Console.

---

### Post by lisati on 2009-04-25
If you've installed Ubuntu with Wubi, it's as simple as uninstalling it with "Add/Remove programs" on the control panel.

---

### Post by fdrake on 2009-04-25
just use a live cd (ubuntu-or other-ones that can boot you pc) and delete all the partitions on the computer. if you just want to make the system stop working just delete all the files instead.

---

### Post by Fallzak on 2009-05-04
> **CatKiller said:**
> If you've got separate partitions and GRUB as your bootloader then you remove the Ubuntu partitions and replace GRUB with Windows' own bootloader with *fixmbr* from Windows' Recovery Console.


got a step by step on how to do this for us less advanced people

---

### Post by CatKiller on 2009-05-05
> **Fallzak said:**
> got a step by step on how to do this for us less advanced people

There's a whole bunch of them on the Internet.

[Here's]("http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/") one of the fist ones that came up on Google.

---

