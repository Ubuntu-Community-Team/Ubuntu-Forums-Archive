---
title: "Wireless drops, won't reconnect on xps m1330 with Ubuntu 7.10"
date: 2008-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamiokande on 2008-07-05
Wireless internet works fine on my m1330 for long periods of time, but then the signal will drop and fail to reconnect. Network Manager also runs very slowly during this period of time, as it attempts to reconnect. If I restart the system, the wireless will reconnect smoothly and everything runs normally.

The wireless output of 'lspci' is:

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

I have looked at the Dell Linux wiki wireless problem ([http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)), but I'm not sure if it applies to me, since I'm not doing any _heavy_ data transfers (it happens while having firefox and pidgin open, but nothing else), so I didn't want to take unnecessary steps. The network connection is somewhat slow, though.

I have run this command:

```
cat /var/log/messages | grep IRQ
```

with the output from an instance of this problem being:

```

Jul  6 10:43:08 localhost kernel: [    7.700029] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul  6 10:43:08 localhost kernel: [    8.141344] ENABLING IO-APIC IRQs
Jul  6 10:43:08 localhost kernel: [    8.624867] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Jul  6 10:43:08 localhost kernel: [    8.624961] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jul  6 10:43:08 localhost kernel: [    8.625052] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Jul  6 10:43:08 localhost kernel: [    8.625143] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Jul  6 10:43:08 localhost kernel: [    8.625237] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jul  6 10:43:08 localhost kernel: [    8.625329] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jul  6 10:43:08 localhost kernel: [    8.625421] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Jul  6 10:43:08 localhost kernel: [    8.625505] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jul  6 10:43:08 localhost kernel: [    8.657980] PCI: Using ACPI for IRQ routing
Jul  6 10:43:08 localhost kernel: [    8.750100] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  6 10:43:08 localhost kernel: [    8.750130] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul  6 10:43:08 localhost kernel: [    8.750158] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jul  6 10:43:08 localhost kernel: [    8.750185] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
Jul  6 10:43:08 localhost kernel: [    9.677500] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  6 10:43:08 localhost kernel: [    3.392000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
Jul  6 10:43:08 localhost kernel: [    3.496000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Jul  6 10:43:08 localhost kernel: [    4.336000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Jul  6 10:43:08 localhost kernel: [    4.444000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Jul  6 10:43:08 localhost kernel: [    4.548000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Jul  6 10:43:08 localhost kernel: [    4.652000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jul  6 10:43:08 localhost kernel: [    6.456000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Jul  6 10:43:08 localhost kernel: [    6.508000]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe4ff800-fe4fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jul  6 10:43:08 localhost kernel: [    6.512000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul  6 10:43:08 localhost kernel: [    7.004000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jul  6 10:43:08 localhost kernel: [    7.004000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
Jul  6 10:43:08 localhost kernel: [    7.324000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Jul  6 10:43:08 localhost kernel: [   14.524000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
```


Perhaps 'level, low' indicates it simply can't find the network?

Any help would be greatly appreciated!! Thanks.

---

### Post by sdennie on 2008-07-06
The Dell wiki link you provided will probably help the problem.  When I ran 7.10 with my XPS m1330, I needed to use those instructions to have anything resembling a stable network connection.  Those instructions may not be complete however.  If you have problems with networking after resuming from suspend, you may have to find the ipw3945 udev rule in /etc/udev/rules.d/70-persistent-net.rules and comment it out.

---

### Post by kamiokande on 2008-07-07
Thanks for your response! I tried making all the changes you mentioned, but it still disconnected afterward. I'm guessing it's just a feeble connection to begin with, and there's nothing that can be done.

---

