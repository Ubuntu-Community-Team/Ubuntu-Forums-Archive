---
title: "Grub help"
date: 2006-07-20
forum: Desktop Environments
---

### Post by afbase on 2006-07-20
is there a way to modify my Grub text through the desktop?
I would also like to know if i could modify it through terminal.

I need to insert 'acpi=off' into my boot script in hopes to remove this error i get:

[xxxxxx.yyyyyy]  ACPI-0674: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[34], disabling event

---

### Post by adam.tropics on 2006-07-21
sudo gedit /boot/grub/menu.lst

...but be careful with it!

---

### Post by vf514 on 2006-07-21
If you mess up your menu.lst for whatever reason but can access a GRUB command line, simply type:

```

grub> root [PARTITION]
grub> kernel /vmlinuz root=[YOUR_ROOT_DEVICE_NODE] ro
grub> initrd /initrd.img
grub> boot

```

where [PARTITION] is the partition Ubuntu lives on (in GNU standard fmt) and [YOUR_ROOT_DEVICE_NODE] is your root device node (I didn't really to explain that, right? haha). If you don't know them, investigate your /boot/grub/menu.lst. They contain commands similar to ones above that GRUB uses by default to boot your system (extra options that are not above should not be necessary). The partition and nodes should be filled in there.

---

