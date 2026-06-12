---
title: "laptop power monitor help"
date: 2005-12-10
forum: Desktop Environments
---

### Post by userlain on 2005-12-10
**system:** Acer Aspire 1691WLMi with i915 centrino chipset

**issue:** The laptop battery power status applet under gnome fails to display how much power I have left on the battery, and whether or not I am using AC power or battery power. 

**background:** In order to get ubuntu to work, i have to add 'noapic nolapic' to the kernel boot options

---

### Post by emperor on 2005-12-10
Your ACPI and battery monitor woes are related to the BIOS on the machine. To fix the problem, a kernel patch and re-compile may be required.

see simliar problem and solution here:
=====================
[http://www.aalbiol.upv.es/ACER.html](http://www.aalbiol.upv.es/ACER.html)

ACPI DSDT patches:
===========
[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)
[http://acpi.sourceforge.net/dsdt/view.php?manufacturer=ACER&name=Aspire+1691WLMi](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=ACER&name=Aspire+1691WLMi)

---

