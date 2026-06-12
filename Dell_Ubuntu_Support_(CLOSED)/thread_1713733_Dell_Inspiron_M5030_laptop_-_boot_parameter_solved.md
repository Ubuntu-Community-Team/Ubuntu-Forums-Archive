---
title: "Dell Inspiron M5030 laptop - boot parameter solved for 10.10"
date: 2011-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AndyCinDallas on 2011-03-24
In short, use **pci=noacpi** as a boot-parameter.

I got up and running successfully using **acpi=off** - but it's not healthy to have ACPI totally disabled, so I did further troubleshooting according to [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) - and here are my results for each one:

> Trouble Booting

For detailed instructions regarding how to modify boot parameters see DebuggingKernelBoot.

   1. Try booting with the "acpi=off" kernel parameter **[COLOR="Red"]This works[/COLOR]**
          * This will disable ACPI support. If the error is the same with ACPI enabled and disabled, this may not be an ACPI issue.
 
   2. If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters:

   Try booting with "acpi=ht" **This doesn't work - it halts on "NET: Registered protocol family 1"**
                * This disables all of ACPI except just enough to enable Hyper Threading. If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code.
 
Try booting with "pci=noacpi" **[COLOR="Red"]This works[/COLOR]**
                * This disables ACPI for IRQ routing and PCI scanning. 

Try booting with "acpi=noirq" **This doesn't work - it halts on "NET: Registered protocol family 1"**
                * This disables ACPI for IRQ routing.
 
Try booting with "pnpacpi=off" **This doesn't work - and gives "ALERT! /dev/sda1 does not exist" - and exits to initramfs**
                * This disables the ACPI component of the Linux Plug and Play code.
 
Try booting with "noapic" **This doesn't work - it halts on "NET: Registered protocol family 1"**
                * Disables the IO-APIC for IRQ routing or PCI scanning.
 
Try booting with "nolapic" **This doesn't work - it halts on "NET: Registered protocol family 1"**
                * Disables the local APIC.

Whichever parameter works for you, make sure to save it:

Open a Terminal window and type: **gksudo gedit /etc/default/grub**

5. Add the parameter (eg. pci=noacpi or whatever) to the end of the relevant line - then hit Save and close the file.

6. Update Grub with the new file - go into Terminal and type: **sudo update-grub** - and it should work fine next time you boot up the laptop.

I hope this helps someone who has the same model of laptop.

---

