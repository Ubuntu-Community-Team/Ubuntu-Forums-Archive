---
title: "DSDT Override for Toshiba Satellite M305D-S4830 Laptops and Similar"
date: 2008-12-27
forum: General Help
---

### Post by Wintervenom on 2008-12-27
If you're having ACPI or CPU scaling issues on the Toshiba Satellite M305D-S4830 laptop or similar, you probably need a DSDT override.

I thought I'd share the override I've created so anyone who is having the same issues won't have to go though the hell of debugging their description tables.

So, here goes...

**EDIT:  Actually, this might not be needed anymore.  Simply adding *acpi_osi="Linux"* to the boot parameters seems to have done away with the ACPI issues..**

---

### Post by GavinX on 2009-03-12
How do you use this? Some instructions would be great. Thanx.

---

### Post by Wintervenom on 2009-03-12
See edit.

---

### Post by sinx on 2009-03-14
**Works in Ubuntu Hardy 8.04?** or Only in 8.10 and 9.04?

---

### Post by Wintervenom on 2009-03-14
> **sinx said:**
> **Works in Ubuntu Hardy 8.04?** or Only in 8.10 and 9.04?

Kernel 2.6.23 and later, so it should work for Hardy, too.

---

### Post by GavinX on 2009-03-14
> **Wintervenom said:**
> 

**EDIT:  Actually, this might not be needed anymore.  Simply adding *acpi_osi="Linux"* to the boot parameters seems to have done away with the ACPI issues..**

I must say thatnks a million. I appended that to my menu.lst and it worked like magic. Again, thanx a million. By the way, I used it on openSuSE 11.1 on my Toshiba Satellite M305D-S4830. So anyone else who has ACPI issues with this machine should find some solace in this fix. :popcorn:

---

### Post by sinxfx on 2009-03-15
Well... , this is my Grub :

kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=8fd7d1f0-7cf1-405e-affa-c3d2dc88111f ro quiet splash acpi_osi="Linux"

But, the Applet "CPU Frequency Monitor" doesnt work... dam!,

its ok?

---

### Post by war_eagle14 on 2009-04-21
Thanks for the update Wintervenom.

---

### Post by shane2peru on 2009-06-16
This has been by far the worst computer I have ever owned and used with Linux.  I have installed Linux on probably 7 different computers, and have always had good results (on occasion minor problems) overall.  I will try this fix on my Tosh Satellite as soon as I'm able to get it to boot again.  A recent kernel update has totally botched my system, and I can't get it to boot at all.  Not even a LiveUSB finishes booting.  Arrgh. 

Shane

---

### Post by shane2peru on 2009-06-16
Ok, I take it back!  I got Jaunty installed, and there wasn't any hangups!  Sound works, wireless works, I haven't tried network card yet (it didn't work in Intrepid), battery is detected (could very well be attributed to the acpi_osi="Linux" fix here).  Over all a much better experience.  ATI drivers seem to look nice over all.  Thanks for the research and fix!  Much appreciated!

Shane

---

