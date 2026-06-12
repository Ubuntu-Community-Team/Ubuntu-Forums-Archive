---
title: "Need to press Enter and hold it to boot ubuntu"
date: 2009-03-08
forum: General Help
---

### Post by Fatdog on 2009-03-08
Hay I have a problem to boot ubuntu, it will not start until i press enter and hold it.

Please help

---

### Post by emad_ramlawi on 2009-03-08
hey iam not really the expert but if ur talking about the grub boot menu u can install this program STARTUP manager it haves alot of options that can effect the bootloader and splash screen :popcorn:

---

### Post by heindsight on 2009-03-08
What exactly happens if you don't press and hold enter?

---

### Post by ftabor on 2009-03-09
I fixed my installation by editing Grub and adding acpi=noirq to the end of the first Kernel statement.

```
sudo nano /boot/grub/menu.lst 
```

Then you can add acpi=noirq to the end of the first kernel statement.

---

