---
title: "IRQ 185 &quot;no one cares!&quot; error in the ubuntu installer"
date: 2005-01-06
forum: General Help
---

### Post by Hyperkick on 2005-01-06
when the system is seting up python libs i get a message about every 3seconds that says: "IRQ 185 no one cares! Disabling IRQ185" 

is it a bug? -and how do i solve the problem?

---

### Post by jdong on 2005-01-06
Someone remind me how many IRQ's the average PC has?  :mrgreen:  :mrgreen:

---

### Post by Rancoras on 2005-01-06
I don't get any google hits at all with any portion of that error message.  Are you sure that's the exact message?  Try googling with the exact error message in quotes.  That has helped me a bunch in the past with errors.

---

### Post by Hyperkick on 2005-01-06
[QUOTE=Rancoras]I don't get any google hits at all with any portion of that error message.  Are you sure that's the exact message?  Try googling with the exact error message in quotes.  That has helped me a bunch in the past with errors.[/QUOTE]

lol, well i have googlet it, and funny enough, it seems peolpe writes questions when they cant google it, dont they?

---

### Post by wallijonn on 2005-01-06
Okay,

go to /var/log

open up the kernel log, kern.log.
scroll through it.

see that IRQ map?
```

[color=blue]Using vector-based indexing
localhost kernel: IRQ to pin mappings:
localhost kernel: IRQ0 -> 0:2
localhost kernel: IRQ1 -> 0:1
localhost kernel: IRQ3 -> 0:3
localhost kernel: IRQ4 -> 0:4
localhost kernel: IRQ5 -> 0:5
localhost kernel: IRQ6 -> 0:6
localhost kernel: IRQ7 -> 0:7
localhost kernel: IRQ8 -> 0:8
localhost kernel: IRQ9 -> 0:9
localhost kernel: IRQ10 -> 0:10
localhost kernel: IRQ11 -> 0:11
localhost kernel: IRQ12 -> 0:12
localhost kernel: IRQ13 -> 0:13
localhost kernel: IRQ14 -> 0:14
localhost kernel: IRQ15 -> 0:15
localhost kernel: IRQ169 -> 0:16
localhost kernel: IRQ201 -> 0:17
localhost kernel: [/color][color=red]IRQ185 -> 0:18[/color][color=blue]
localhost kernel: IRQ177 -> 0:19
localhost kernel: IRQ193 -> 0:23[/color]

```
it should say somewhere else:
```
[COLOR=Blue]PCI: Using ACPI for IRQ routing
IRQ185 -> 0:18
```
[/COLOR]
scroll through it some more.

you should find a line that looks like this: 
```

[COLOR=Blue]**ACPI**: PCI interrupt 0000:[/color][color=red]00:1f.1[/color][color=blue][A] -> GSI 18 (level, low) -> **IRQ 185**[/COLOR]

```
So, this is telling me that IRQ 185 is associated with ACPI.

But wait, there's more:
```

[COLOR=Blue]APCI: PCI interrupt 0000:[/color][color=red]00:1d.2[/color][color=blue][C] -> GSI 18 (level, low) -> **IRQ 185**
ACPI: PCI interrupt 0000:[/color][color=red]02:01.0[/color][color=blue][A] -> GSI 18 (level, low) -> **IRQ 185**
ACPI: PCI interrupt 0000:[/color][color=red]03:03.2[/color][color=blue][ B ] -> GSI 18 (level, low) -> **IRQ 185**
[/COLOR]

```
Notice how they are all at GSI level 18?

So let's look for all the lines that end with "IRQ 185"...

scroll some more and you should see something like this:

```

[COLOR=Blue]ACPI: PCI interrupt 0000:00:_1d.2_[C] -> GSI 18 (level, low) -> **IRQ 185**
uhci_hcd 0000:[/color][color=red]00:1d.2[/color]: [COLOR=darkgreen]Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI[/COLOR] [color=blue]#3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:[/color][color=red]00:1d.2[/color][color=blue]: irq 185[/U], io base 0000e800
uhci_hcd 0000:00:1d.2: _new USB bus registered_, assigned bus number 3
hub 3-0:1.0: _USB hub found_
hub 3-0:1.0: _2 ports detected_
usb 2-2: new low speed USB device using address 2[/COLOR]

```

Scroll down some more. You may see something like this:
```

[COLOR=Blue]ACPI: PCI interrupt 0000:[/color][color=red]02:01.0[/color][color=blue][A] -> GSI 18 (level, low) -> **IRQ 185**
PCI: Setting latency timer of device 0000:02:01.0 to 64
e1000: eth0: e1000_probe: [/color][color=darkgreen]Intel(R) PRO/1000 Network Connection[/COLOR]

```

but wait, there's more:

```

[COLOR=Blue]ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:[/color][color=red]03:03.2[/color][color=blue][ B ] -> GSI 18 (level, low) -> **IRQ 185**
ohci1394: fw-host0: [/color][color=darkgreen]OHCI-1394 1.1[/color][color=blue] (PCI): IRQ=[185][/U]  MMIO=[ff904000-ff9047ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c00200021ea]
e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex[/COLOR]

```

So, not only do I have a USB hub on software IRQ 185, but I also have my NIC card and firewire. All the devices are controlled by ACPI (like "wake-on-lan", "wake-on-mouse-movement", disk cycle down, etc).

Now, remember that first line we looked at, that "00:1f.1"? 
```

[COLOR=Blue]PCI: Ignoring BAR0-3 of _IDE controller_ 0000:00:1f.1
ACPI: PCI interrupt 0000:[/color][color=red]00:1f.1[/color][color=blue][A] -> GSI 18 (level, low) -> **IRQ 185**
**ICH5**: [/color][color=darkgreen]IDE controller[/color][color=blue] at PCI slot 0000:[/color][color=red]00:1f.1[/color][color=blue]
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)[/COLOR]

```

You should also see this, somewhere:
```

[color=blue]ACPI: (supports S0 S1 S4 S5)
ACPI wakeup devices: 
TANA P0P3 AC97 USB0 USB1 USB2 USB3 USB7 SLPB[/color] 

```

So, we end up with this as a device map:[size=3]
```

ACPI: PCI interrupt 0000:00:1f.1 IRQ 185 [COLOR=Red]ICH5 IDE Disk Controller[/COLOR]
APCI: PCI interrupt 0000:00:1d.2 IRQ 185 [COLOR=blue]USB Hub[/COLOR]
ACPI: PCI interrupt 0000:02:01.0 IRQ 185 [COLOR=darkred]Intel Pro 1000 NIC[/COLOR]
ACPI: PCI interrupt 0000:03:03.2 IRQ 185 [COLOR=royalblue]1394 Firewire[/COLOR][/SIZE]

```

[http://vizzzion.org/?id=acpi_sleep](http://vizzzion.org/?id=acpi_sleep)

now, let's look at /var/log/syslog...

Any more than this and you'll have to send me some money. :D

--------------------------------------------------------------------------------------------------------
[size=3]
The first thing to do is remove all the USB devices (like USB printers, USB speakers, USB game controllers, etc.) & firewire devices, memory sticks and memory cards, etc., when installing Ubuntu. If it still fails, then move the USB mouse to the PS/2 port using the mouse adapter which came with your mouse. 

Try again.

If it still fails, then disable the USB ports in the BIOS.
If it still fails, then disable ACPI in the BIOS but enable USB.
If it still fails, then disable ACPI & USB.
Id it still fails, chances are that it is the South Bridge Controller is not supported (like SUS or Promise disk drive controllers).

One of the easiest things to hose a system install over is a "software" modem; otherwise known as "WinModems". Remove that PCI modem from your system, enable ACPI & USB and try again.

Oh, you forgot you had one in your system? It came with your system when you first bought it but you never used it? You're on cable now, hm? I see...

btw, if you're using an USB cable or DSL modem ... You're sucking pond water... You're going to drown unless you connect it to your J45 NIC connection, which means you'll have to buy a PCI NIC card. 

That's right - disconnect any USB modems when installing Ubuntu (or any Linux). It may not see it, and if it sees it, then it may hose the install.[/size]

I think I've put enough work into this to open up a how to, no? :D

---

