---
title: "IRQ Sharing Conflict with Network and Sound cards"
date: 2006-01-08
forum: General Help
---

### Post by kairu0 on 2006-01-08
I have been struggling with my wireless network card (pcmcia, using the rt2500 driver) and my sound card (Intel HDA) trying to share the same interrupt. They both work as is, but the problem is that network traffic creates noise in the speakers.

My BIOS has nothing about IRQ sharing, PnP OSs, or anything like it, so I think it will be up to Linux to solve the problem.

Here are my IRQs at the moment:

```
~$ cat /proc/interrupts
           CPU0
  0:    3215915    IO-APIC-edge  timer
  1:       6290    IO-APIC-edge  i8042
  8:          1    IO-APIC-edge  rtc
  9:       1364   IO-APIC-level  acpi
 11:          1    IO-APIC-edge  sonypi
 12:        136    IO-APIC-edge  i8042
 14:      65238    IO-APIC-edge  ide0
 16:     514399   IO-APIC-level  uhci_hcd:usb4, HDA Intel, yenta, i915@pci:0000:00:02.0, ra0
 18:          3   IO-APIC-level  uhci_hcd:usb3, ohci1394
 19:          0   IO-APIC-level  uhci_hcd:usb2
 20:       1590   IO-APIC-level  eth0
 23:     142872   IO-APIC-level  uhci_hcd:usb1, ehci_hcd:usb5
NMI:          0
LOC:     714532
ERR:          0
MIS:          0

```

HDA intel (sound) and ra0 (network) are trying to share IRQ 16.

Can I disable IRQ sharing or force either my sound card or network card to use a different IRQ? Any other ideas?

---

### Post by kairu0 on 2006-01-10
Just found pci=biosirq, but it didn't solve the problem.

---

