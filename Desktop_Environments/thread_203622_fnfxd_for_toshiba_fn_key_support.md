---
title: "fnfxd for toshiba fn key support"
date: 2006-06-25
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-06-25
I'm trying to use the fnfxd deamon to enable my fn key on my toshiba laptop, but when i try starting the deamon, I get this.

> stian@stian-laptop:~$ sudo fnfxd
Password:
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).


I've seen other people with this issue, but no solution. When the error tells me that I need to have the toshiba option enabled in the ACPI section in the kernel, my question is, where and how do I edit the kernel/ACPI section with the Toshiba option? Is it like editing a text file, or is it more complicated? Where's the file i need to edit situated?

---

### Post by raptros-v76 on 2006-06-25
you need the fnfx, toshset, and toshutils packages installed

---

### Post by art on 2006-06-25
What kind of BIOS do you have. This utility does not work on all model... If your BIOS is not a TOSHIBA developed one, it will probably not work.

---

### Post by imrcly on 2006-08-25
I am having this same problem it does not find the toshiba acpi, i have verified I have the Toshiba bios, the only thing i can find is the toshiba acpi is put in when the kernal is compiled  can anyone confirm this, because everything i have found the current ubuntu kernal already has the support for it

---

### Post by SonicTheHedgehog on 2007-02-16
*bump*

How do I enable the Toshiba options in the kernel, so I can use fnfxd?

---

### Post by Neo0351 on 2007-07-21
I'm having the same problem.  I have a Toshiba Satellite A-65 and I've installed fnfxd, toshset, toshutils and I'm still getting the same error.  Anyone know who to enable the Toshiba support for the kernel?  Oh, I'm running both Ubuntu 7.06 and 7.10 and I can't get it working on either install.

---

### Post by Cauda_Draconis on 2007-09-22
I'm having that problem too. I boot up, and it comes up with a dialogue that says "Add host" (I tried clicking on the help button, but I've got this weird problem where my pre-logged-in fonts are about 100pt or something and I don't know how to fix it, so I can't see all the help dialogue), then I press ctrl-alt-F1 to go to command line, and it tells me that it can't open /proc/acpi/toshiba/keys and that my kernel has to have the Toshiba option enabled.

I found some instructions on [http://fnfx.sourceforge.net/index.php?section=doc](http://fnfx.sourceforge.net/index.php?section=doc), and I'm going to try them out. I'll report on how they work once I've tried them

---

