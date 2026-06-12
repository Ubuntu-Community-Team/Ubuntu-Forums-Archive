---
title: "Installation problem PS/2 controller"
date: 2005-12-30
forum: General Help
---

### Post by Flyby on 2005-12-30
Hy, I'm new to ubuntu (and almost new to linux).

I'm trying to install ubuntu on a system with following specs:

a Packard Bell Spirit with
pentium III 500 Mhz, 128 MB SDram
motherboardname: NEC G7CRV
standard microsoft natural keyboard PS/2
standard logitech wheelmouse PS/2

I can boot from the install cd but when i start the default installation, the process halts or freezes during the hardware detection after following line:
PNP: PS/2 controller [PNP0303: PS2K, PNP0f13: PS2M] at 0x60, 0x64 irq 1,12
the cursorline is still blinking under it but the installation stops (CD stops spinning, waited for an hour or so, nothing happened) and there is no keyboardreaction (num lock, caps lock, scrolllock)

I tried again with 'noapic', 'nolapic', 'pci=routeirq', nothing worked
I tried installing 'server', same problem

any id's?

grtz

---

### Post by Flyby on 2005-12-30
Ok, it seemed to be the same problem as someone else on this forum.
Disabled USB-keyboard support in BIOS settings and the installation proceeded normally

grtz

---

