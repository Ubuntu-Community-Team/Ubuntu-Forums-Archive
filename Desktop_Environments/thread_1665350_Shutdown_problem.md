---
title: "Shutdown problem"
date: 2011-01-12
forum: Desktop Environments
---

### Post by elldirash on 2011-01-12
On my Desktop, whenever i try to shutdown, the system stop the disks, but leaves the screen on and the fans running. It leaves the message

[     367.604109] Power Down

on the screen, with the number being different from time to time. This is also the final output with the --debug kernel option on.

I have tried various fixes to similar power problems that i've found, e.g. adding apm power_off=1 to /etc/modules but none have seemed to work so far. I'm relatively new to Linux so any help would be greatly appreciated.

---

### Post by mister_p_1998 on 2011-01-12
> **elldirash said:**
> On my Desktop, whenever i try to shutdown, the system stop the disks, but leaves the screen on and the fans running. It leaves the message

[     367.604109] Power Down

on the screen, with the number being different from time to time. This is also the final output with the --debug kernel option on.

I have tried various fixes to similar power problems that i've found, e.g. adding apm power_off=1 to /etc/modules but none have seemed to work so far. I'm relatively new to Linux so any help would be greatly appreciated.

I think you need to add to the line in grub where it says the kernel ACPI=off on the end if I remember rightly. Is it an old PC? they have problems with shutting down properly..
see here:
Kernel Options

Note: These options are used by the kernel, and will apply to any installation at any time. The file "Documentation/kernel-parameters.txt" in the relevant linux-source package provides more information.

Option
	

Impact

vga=xxx
	

Set your framebuffer resolution to VESA mode xxx. Check here for a list of possible modes.

acpi=off OR noacpi
	

This parameter disables the whole ACPI system. This may prove very useful, for example, if your computer does not support ACPI or if you think the ACPI implementation might cause some problems (for instance random reboots or system lockups).

acpi=force
	

Activates the ACPI system even if your computer BIOS date is older than 2000. This parameter overrides acpi=off and can also be used with current hardware if the ACPI support is not activated despite apm=off.

pci=noacpi OR acpi=noirq
	

These parameters disable the PCI IRQ routing

pci=acpi
	

This parameter activates the PCI IRQ routing

acpi_irq_balance
	

ACPI is allowed to use PIC interrupts to minimize the common use of IRQs.

acpi_irq_nobalance
	

ACPI is not allowed to use PIC interrupts.

acpi=oldboot
	

Deactivates the ACPI system almost completely; only the components required for the boot process will be used.

acpi=ht
	

Impact Deactivates the ACPI system almost completely; only the components required for hyper threading will be used.

noapic
	

Disable the "Advanced Programmable Interrupt Controller (APIC)".

nolapic
	

Disable the "local APIC".

apm=off OR noapm
	

Disable the Advanced Power Management.

irqpoll
	

Changes the way the kernel handles interrupt calls (set it to polling). Can be useful in case of hardware interrupt issues.

acpi.power_nocheck=1 OR acpi_osi=linux
	

Disable the check of power state or changes the OS compatibility reported to the BIOS. Necessary on some broken BIOSes to make temperature/fan control work. 


Original link here:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by elldirash on 2011-01-12
Thanks for the reply.

No the acpi=off option is not set. I tried the acpi=force option but that didn't solve the problem either. It is not a very old machine. It's a Core 2 Duo E8400 on a ASRock ConRoe1333-esata2 motherboard. Im running dualboot and it shuts down neatly from Windows XP.

---

### Post by elldirash on 2011-01-14
No one has any clues as to finding the problem with this?

---

### Post by elldirash on 2011-01-14
No one has any clues as to finding the problem with this?

---

### Post by elldirash on 2011-01-14
Today i solved the problem. By the tiresome  process of disabling random stuff in BIOS i pinpointed the problem to be with the onboard firewire module. Disabling this  in BIOS solved the problem and the system now shuts down properly.

---

