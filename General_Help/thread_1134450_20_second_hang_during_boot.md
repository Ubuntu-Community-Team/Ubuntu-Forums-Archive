---
title: "20 second hang during boot"
date: 2009-04-23
forum: General Help
---

### Post by kermat on 2009-04-23
Hi all

I am experiencing an annoying 20-second hang during boot time. The progress bar stops and it seems the system is not doing anything but waiting for a timeout to be reached. I have been having this problem for a while now, and although I'm now using Jaunty with the 2.6.28 kernel, the same problem dates back to (at least) Hardy.

Here are (what I believe) the relevant lines in dmesg:
```

...
[   25.095741] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   25.095748] HDA Intel 0000:00:06.1: PCI INT B -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   25.095819] HDA Intel 0000:00:06.1: setting latency timer to 64
[   25.124571] usbcore: registered new interface driver snd-usb-audio
[   43.725171] lp0: using parport0 (interrupt-driven).
[   43.893819] Linux video capture interface: v2.00
[   43.945080] em28xx: Unknown parameter `device_mode'
[   43.985830] w83627ehf: Found W83627EHG chip at 0xa10
...

```

What would be the next step to further analyze the problem and get it (finally) fixed?
Thanks
-- 
kermat

---

### Post by cariboo on 2009-04-23
If you unplug your usb sound device does the problem go away?

---

### Post by kermat on 2009-04-24
Sadly, it didn't change much...

```

...
[   25.178932] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   25.178939] HDA Intel 0000:00:06.1: PCI INT B -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   25.179003] HDA Intel 0000:00:06.1: setting latency timer to 64
[   43.875906] lp0: using parport0 (interrupt-driven).
[   44.053289] Linux video capture interface: v2.00
[   44.103164] em28xx: Unknown parameter `device_mode'
[   44.168961] w83627ehf: Found W83627EHG chip at 0xa10
...

```

By the way, I realize lp0 and parport0 are related but parallel ports, but my computer doesn't have one. Could it be an explanation?

---

### Post by dcstar on 2009-04-24
> **kermat said:**
> Sadly, it didn't change much...
........
By the way, I realize lp0 and parport0 are related but parallel ports, but my computer doesn't have one. Could it be an explanation?

Then disable the parallel port in the BIOS.

---

### Post by kermat on 2009-04-24
Ok,

I did that, then there was an error from lp and the hang was even longer (around 50 seconds):
```

[   73.801500] lp: driver loaded but no device found

```So I also tried to comment out the "lp" module from /etc/modules. I actually also commented out other modules I don't need right now (related to a usb video device).

The error in dmesg disappeared, but the hang is still there, and it is still 50 seconds...

---

