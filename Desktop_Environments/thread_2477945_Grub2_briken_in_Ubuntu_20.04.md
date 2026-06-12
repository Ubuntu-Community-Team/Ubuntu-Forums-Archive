---
title: "Grub2 briken in Ubuntu 20.04?"
date: 2022-08-12
forum: Desktop Environments
---

### Post by nibal on 2022-08-12
Hi,

I try to configure grub2 for a dual boot environment with Ubuntu & Windows.
Seems that grub-mkconfig no longer reads /etc/default/grub.d/*
Also when I use:
GRUB_DISABLE_OS_PROBER=true in /etc/default/grub,
it still probes and loads a BIOS-disabled OS:(

Nikos

---

### Post by yancek on 2022-08-12
Which release of windows do you have?  Is windows installed in UEFI mode?  Is Ubuntu installed in UEFI mode?  Is this a new install of Ubuntu?  Have you been able to boot both Ubuntu and windows from the Grub bootloader or has it never worked.  You can run the command:  sudo parted -l to list partitions and you should see an EFI partition if you have one.  If you do, mount it to see if you have entries for ubuntu and Microsoft.

The Grub bootloader if installed in Legacy mode will not boot a UEFI install of windows so check that first.

---

### Post by nibal on 2022-08-12
> **yancek said:**
> Which release of windows do you have?  Is windows installed in UEFI mode?  Is Ubuntu installed in UEFI mode?  Is this a new install of Ubuntu?  Have you been able to boot both Ubuntu and windows from the Grub bootloader or has it never worked.  You can run the command:  sudo parted -l to list partitions and you should see an EFI partition if you have one.  If you do, mount it to see if you have entries for ubuntu and Microsoft.

The Grub bootloader if installed in Legacy mode will not boot a UEFI install of windows so check that first.

he Grub bootloader if installed in Legacy mode will not boot a UEFI install of windows so check that first.[/QUOTE]

This is a fresh install of both in my new disk, after my old one died:(
I don;t see the windows partition in grub bootmenu, just the ubuntu +memstests...
I do have an EFI partition.
ls EFI/
-> Boot/ Microsoft/
ls EFI/Microsoft.
->Boot

Seems my ubuntu is in legacy mode. I will have to reinstall it in EFI mode:)

Thanks

---

