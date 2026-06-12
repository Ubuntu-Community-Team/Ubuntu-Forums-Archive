---
title: "Boot Errors (AMD 64 ASUS M2N32-SLI Deluxe 4GB RAM)"
date: 2009-04-26
forum: General Help
---

### Post by CarlDog on 2009-04-26
Installed 9.04 the other day and am noticing errors flashing across my screen on startup. I'm able to load up and run everything fine, but I'm concerned that I should be doing something to fix them.

The first one was the iommu error that seems to be pretty standard, but I've had no luck resolving it thus far. After digging through the logs, I'm also noticing this:
```
[   11.601939] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[   11.602084] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

```I'm also getting ACPI errors starting around 1.027 where they expect a reference and found 0.

Have noticed that sleep doesn't seem to be working properly, so I'm assuming that's also tied into it somehow.

BTW, I'm a new linux user. Be gentle. I learn quickly, but do your best to explain it thoroughly. :)

EDIT: Whoops forgot to put in the last ACPI error log entry:

```
[    1.032097] ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference [20080926]
[    1.032102] ACPI: Expecting a [Reference] package element, found type 0
```

---

### Post by KaffeeJunky on 2010-01-25
Even thought this is a very old thread I'm experincing a similar error on startup, since I've patched my M2N32SLI Deluxe's bios to the latest stable version wich is 2205

The errors are the following:
> 
[Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
>  ACPI: I/O resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
>  
 ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference [20080926]
 ACPI: Expecting a [Reference] package element, found type 0

Since the BIOS Update I haven't been able to dynamically clock the cpu without enabling AMDs Cool&Quiet feature in the bios, also the boot time increase a bit, it seems to take some time to process the ACPI Exceptiong a Reference package element thingy, other then that the overall performance of my system increased, so a bios version rollback doesn't seem to be a valid option.

Edit: I'm also using Ubuntu 9.04

---

