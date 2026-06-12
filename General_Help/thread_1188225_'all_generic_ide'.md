---
title: "'all_generic_ide'"
date: 2009-06-15
forum: General Help
---

### Post by GingersK on 2009-06-15
Hi guys

I recently switched from Fedora to Ubuntu. In the process I encountered a few problems with installation. I managed to overcome this by installing ubuntu 8.10, which was only possible by the inclusion of "all_generic_ide" in the boot parameters, then once this was done to upgrade to 9.04. However, for ubuntu to boot it still requires me to manually add "all_generic_ide" at every load.

To this end, I have 2 questions that I'd appreciate some advice on.

1) What exactly does "all_generic_ide" do, and will using it cause any undesirable side effects with my ubuntu installation?

2) If the effects are minimal, how can I alter the system to automatically boot with "all_generic_ide" without having to manually add the parameter at every single boot. 



Thanks Guys

Kurt

---

### Post by plucky on 2009-06-17
> 1) What exactly does "all_generic_ide" do, and will using it cause any undesirable side effects with my ubuntu installation?

Not really sure,but I think it loads a different set of drivers for your sata/pata hard disk drives.

> 2) If the effects are minimal, how can I alter the system to automatically boot with "all_generic_ide" without having to manually add the parameter at every single boot.


Open a terminal **Applications > Accessories > Terminal** and input ```
gksudo gedit /boot/grub/menu.lst
``` and scroll down to find the boot line and add "all_generic_ide" 

e.g.
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro quiet splash [color=blue]all_generic_ide[/color] 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

and in the same file add it to the "options" section

e.g.
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [color=blue]all_generic_ide[/color]

```

so that it will still be there after a kernel update.

Good Luck

---

### Post by GingersK on 2009-06-17
That worked brilliantly, thank you very much.

Kurt

---

