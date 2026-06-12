---
title: "Laptop locks up on every boot and power button gets past it"
date: 2008-12-31
forum: General Help
---

### Post by dmorlow on 2008-12-31
It's a wierd issue.  I'm running the latest version of ubuntu.  I tried both 32 and 64 bit versions and same thing.  When I boot the computer and it's at the splash screen where the horizontal bar progresses across the screen, every boot up, the bar freezes and I have to hold down the power button (longer than a quick push but not too long as it would turn the computer off.). But when I hold it down for about 2 seconds, the computer wakes back up and finishes booting.  Any ideas how to fix this?

---

### Post by Ahadiel on 2008-12-31
Are you by chance using an HP or Compaq laptop?

Find the "kernel" line of the kernel you're trying to boot in /boot/grub/menu.lst, and append 'acpi=noirq' to the end of the line.

---

