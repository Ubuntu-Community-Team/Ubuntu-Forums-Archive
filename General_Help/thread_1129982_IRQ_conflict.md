---
title: "IRQ conflict"
date: 2009-04-19
forum: General Help
---

### Post by cyberkest on 2009-04-19
Hello! 
Please help with this kind of problem: I have Digium WildCard TE121 and dmesg shows me: "[135.397186] wcte12xp0: Missed interrupt. Increasing latency to 5 ms in order to compensate." 
What can I do in my situation?

root@pbx:~# cat /proc/interrupts
           CPU0       CPU1
  0:        135          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          5          0   IO-APIC-edge
  7:          0          0   IO-APIC-edge      parport0
  8:         62          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:      30005          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:    2950549          0   IO-APIC-fasteoi   wcte12xp0, i915@pci:0000:00:02.0
 17:      30090          0   IO-APIC-fasteoi   uhci_hcd:usb2, eth0
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 19:       1399          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 23:      12364          0   IO-APIC-fasteoi   ata_piix
NMI:          0          0   Non-maskable interrupts
LOC:      73984      83760   Local timer interrupts
RES:       2492       1880   Rescheduling interrupts
CAL:        101      28781   function call interrupts
TLB:        454        798   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

---

### Post by dcstar on 2009-04-20
> **cyberkest said:**
> Hello! 
Please help with this kind of problem: I have Digium WildCard TE121 and dmesg shows me: "[135.397186] **wcte12xp0**: Missed interrupt. Increasing latency to 5 ms in order to compensate." 
What can I do in my situation?

root@pbx:~# cat /proc/interrupts
           CPU0       CPU1
.........
** 16:    2950549          0   IO-APIC-fasteoi   wcte12xp0, i915@pci:0000:00:02.0**
.........

Go into your BIOS and move the i915 video card to another interrupt.

---

