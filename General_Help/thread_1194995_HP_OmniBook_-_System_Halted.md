---
title: "HP OmniBook - System Halted"
date: 2009-06-23
forum: General Help
---

### Post by shooterjames on 2009-06-23
Hi

I have just installed 9.04 on an old HP OmniBook Pentium 3 252Mb Ram i had knocking around which i was going to give to my father in law. The install went fine and all was good but when i go to shut down instead of turning off after the Ubuntu Graphic i get a black screen with the following displayed:

[768.596931] System Halted.

nothing else appears on the screen, the restart command is successful the laptop turns off and back on again. I think maybe its toast as i said it was knocking around.

Any help is much appreciated.
thanks

---

### Post by kerry_s on 2009-06-23
you just need to add a setting to the kernel options in /boot/grub/menu.lst

i can't remember the exact command right now, it's something like "shutdown=power_off" or something, i'll have to google it and get back to you.

from i can see it looks like it works best with apm.

press> **alt+f2**
type> **gksudo mousepad /boot/grub/menu.lst**

look for the line that starts with "kernel" go to the end and add: **acpi=off apm=on**

should look something like this:
**kernel		/boot/vmlinuz-2.6.26-2-686 root=UUID=dfa7a362-0d42-4784-bdc9-ae6171291c90 ro vga=791 acpi=off apm=on**

it won't look exactly like mine, no 2 systems are the same. :)

---

### Post by shooterjames on 2009-06-23
> **kerry_s said:**
> you just need to add a setting to the kernel options in /boot/grub/menu.lst

i can't remember the exact command right now, it's something like "shutdown=power_off" or something, i'll have to google it and get back to you.

from i can see it looks like it works best with apm.

press> **alt+f2**
type> **gksudo mousepad /boot/grub/menu.lst**

look for the line that starts with "kernel" go to the end and add: **acpi=off apm=on**

should look something like this:
**kernel		/boot/vmlinuz-2.6.26-2-686 root=UUID=dfa7a362-0d42-4784-bdc9-ae6171291c90 ro vga=791 acpi=off apm=on**

it won't look exactly like mine, no 2 systems are the same. :)

:D Spot on thanks very much, i will give it a try and get back to you!!

thanks again:D

---

### Post by timzak on 2009-06-27
Found this solution that worked for me:

```
gksudo gedit /etc/modules
```

Add the following line to the bottom of the file, save, and reboot:

> apm power_off=1

---

### Post by shooterjames on 2009-07-02
> **timzak said:**
> Found this solution that worked for me:

```
gksudo gedit /etc/modules
```

Add the following line to the bottom of the file, save, and reboot:

Thanks both for your help, timzak's fix worked for me.

Brill thanks:p

---

