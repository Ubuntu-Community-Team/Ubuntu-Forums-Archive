---
title: "Problem installing Kubuntu on my friends computer."
date: 2005-07-20
forum: Desktop Environments
---

### Post by ihavenohalo641 on 2005-07-20
I get the messege

ohci-hcd 0000:00:13.0: Unlink after no IRQ? Different ACPI or APIC settings may help

I did't experience this problem on either of my home computers. Any hep would be greatly appreciated.

---

### Post by varunus on 2005-07-20
What type of computer does your friend have?  Try loading the installer with the "noapic" option.  (I think you would type "linux noapic" at the installer prompt, but make sure by looking in the installer help by hitting F2 or F3, i think)

---

### Post by ihavenohalo641 on 2005-07-20
He's using a HP Pavilion a1130n. I will try what you suggested and post the results in a few moments.

---

### Post by ihavenohalo641 on 2005-07-20
Same results as before. Grrrrr ](*,)

---

### Post by az on 2005-07-20
"Different ACPI or APIC settings may help"

Can you adjust power management (or disable it) in BIOS?

Hoary works as well with apm...

---

### Post by ihavenohalo641 on 2005-07-20
How would you do that?

---

### Post by derrick1985 on 2005-07-20
[QUOTE=ihavenohalo641]How would you do that?[/QUOTE]

In the bios. On HP computers I think it's hit F1 when the hp boot screen is shown.

search hp.com with the model number of the hp pc to find out.

---

### Post by az on 2005-07-20
[QUOTE=ihavenohalo641]How would you do that?[/QUOTE]

If not F1, then F10, del, Escape... play around...

---

### Post by ihavenohalo641 on 2005-07-21
Okay. I've now gotten past that error by screwin with the I/O device configuration, but now it doesn't detect my harddrive. GRRRRRR ](*,)

---

### Post by rmjokers on 2005-07-21
FYI...ohci-hcd is a kernel module that deals with USB support in the kernel.  Did you have any unusual devices plugged into a USB port that might have contributed to this problem?  Also, I noticed that the machine you are working on has a SATA hard drive.  It might be worthwhile to search for problems with the particular chipset the machine has to see if linux works with the SATA controller since this is relatively new technology.

---

