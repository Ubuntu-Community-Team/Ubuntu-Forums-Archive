---
title: "The module that would not die"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Kashirigi on 2006-08-28
Hi,

I'm having the same problem many laptop users are -- acpi_sbs causes keyboard  problems. As I don't particularly care about my battery status because I'm usually plugged in, I just want to remove acpi_sbs.

So . . .

acpi_sbs is in /etc/modprobe.d/blacklist

I've added rmmod acpi_sbs to /etc/rc.local

I've added a symlink to /etc/rcS.d
 S80rc.local -> ../rc.local

So, acpi_sbs STILL LOADS!

Am I missing something?

---

### Post by Metacarpal on 2006-08-28
Not sure about killing off that one specific module, but here's something that could possibly solve your woes...

Edit /boot/grub/menu.lst to add:
```
pci=noacpi
```

---

### Post by Kashirigi on 2006-08-28
WTF! Many reboots later, and now acpi_sbs is no longer there!

I suppose I shouldn't complain.

Maybe it just really liked my computer and didn't want to go.

---

### Post by Metacarpal on 2006-08-28
Had a houseguest like that once...

---

