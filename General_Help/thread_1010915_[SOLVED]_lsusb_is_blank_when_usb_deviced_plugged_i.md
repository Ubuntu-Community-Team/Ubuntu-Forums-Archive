---
title: "[SOLVED] lsusb is blank when usb deviced plugged in"
date: 2008-12-14
forum: General Help
---

### Post by DefyPhysics on 2008-12-14
I just recently moved my main desktop to ubuntu and am now totally windows free!  However, a major problem has risen.  Normally the breadth of knowledge already available has solved other people's problems throughout the internet and is accessible through google (thus solving my problems).  This has stumped me though.  

When I plug in any USB device, it does not show up.  The usb device IS getting power.  Here is what I've tried:

1. I've checked bios, even though I haven't messed with anything since installing ubuntu and windows detected USB devices.
2. lsusb outputs NOTHING.
casey@ooboontoo:~$ lsusb
casey@ooboontoo:~$
3. dmesg shows nothing related to USB at all.
4. I've tried all USB ports with different devices.  Front, back. Printer, usb drive, ipod.  I know at the very least my usb drive should work because it has worked in the past with dual boot.

The only other possible confliction is that I have to turn ACPI off to boot, and I've heard ACPI is finicky with USB.  Any ideas would be excellent! Thanks.

---

### Post by sedawk on 2008-12-14
Check for strings "usb, ehci, ohci" in the output of
1) lspci (should list your USB controller)
2) dmesg (detection not working, communication broken)
3) lsmod (any usb modules loaded)

Use the output from 1) to search the web and see if there is a general 
problem with your controller with linux.

---

### Post by DefyPhysics on 2008-12-14
> **sedawk said:**
> Check for strings "usb, ehci, ohci" in the output of
1) lspci (should list your USB controller)
2) dmesg (detection not working, communication broken)
3) lsmod (any usb modules loaded)

Use the output from 1) to search the web and see if there is a general 
problem with your controller with linux.

1)
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

2) 
[    4.497355] ohci_hcd 0000:00:13.0: can't find IRQ for PCI INT A; probably buggy MP table
[    4.497355] ohci_hcd 0000:00:13.0: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.0 setup!
[    4.497355] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -19
[    4.497355] ohci_hcd 0000:00:13.1: can't find IRQ for PCI INT B; probably buggy MP table
[    4.497355] ohci_hcd 0000:00:13.1: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.1 setup!
[    4.497355] ohci_hcd 0000:00:13.1: init 0000:00:13.1 fail, -19
[    4.497355] ohci_hcd 0000:00:13.2: can't find IRQ for PCI INT C; probably buggy MP table
[    4.497355] ohci_hcd 0000:00:13.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.2 setup!
[    4.497355] ohci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[    4.497355] ohci_hcd 0000:00:13.3: can't find IRQ for PCI INT B; probably buggy MP table
[    4.497355] ohci_hcd 0000:00:13.3: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.3 setup!
[    4.497355] ohci_hcd 0000:00:13.3: init 0000:00:13.3 fail, -19
[    4.497355] ohci_hcd 0000:00:13.4: can't find IRQ for PCI INT C; probably buggy MP table
[    4.497355] ohci_hcd 0000:00:13.4: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.4 setup!
[    4.497355] ohci_hcd 0000:00:13.4: init 0000:00:13.4 fail, -19
[    4.497355] ehci_hcd 0000:00:13.5: can't find IRQ for PCI INT D; probably buggy MP table
[    4.497355] ehci_hcd 0000:00:13.5: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.5 setup!
[    4.497355] ehci_hcd 0000:00:13.5: init 0000:00:13.5 fail, -19

3) usbcore               148848  2 ehci_hcd,ohci_hcd

That is the only thing usb related I could see.

---

### Post by sedawk on 2008-12-14
Okay, one of my computers shows the same list as yours does (list 1)

But here the second list looks different:
[    2.369943] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[    4.256235] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.256250] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.256277] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2

I'm using default boot parameters here.
I have a laptop here that freaks out on USB when giving the
wrong acpi parameter (apci=force ?).
So play around with apic again or search the web looking for
your specific computer model and USB/acpi.

---

### Post by DefyPhysics on 2008-12-15
> **sedawk said:**
> Okay, one of my computers shows the same list as yours does (list 1)

But here the second list looks different:
[    2.369943] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[    4.256235] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.256250] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.256277] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2

I'm using default boot parameters here.
I have a laptop here that freaks out on USB when giving the
wrong acpi parameter (apci=force ?).
So play around with apic again or search the web looking for
your specific computer model and USB/acpi.

My boot parameter for ACPI is ACPI=off, otherwise the computer hangs on bootup with a flashing underscore. 

If there are other options for ACPI, that might work... but I do not know those options.  I will do some research though. Thanks!

---

### Post by DefyPhysics on 2008-12-15
I figured out what was wrong.  It was definitely a confliction with my motherboard's ACPI feature and USB. My motherboard is an ASUS M2A-VN.  All that was needed was a bios flash to the most updated version.  This fixed the issue!

---

