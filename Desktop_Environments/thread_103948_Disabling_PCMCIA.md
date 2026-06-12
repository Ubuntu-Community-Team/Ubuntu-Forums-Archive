---
title: "Disabling PCMCIA"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Coyne on 2005-12-15
Owkey, I have the 5.10 version now, but still it hangs with the Starting Hotplug... But I can skip that. But now another thing comes up. When "Starting PCMCIA services" comes up, it hang again, and I can't skip that.
I can't get in the single mode and neither can I get in the recovery mode, can someone help me ???
In text it gives some error about : hw_random: RNG not ...
Maybe this can help you ...

---

### Post by 23meg on 2005-12-15
Choose the kernel you'd like to boot in GRUB, hit e, choose the main kernel like, hit e again, put this option at the end of it ```
pcmcia=no
```hit enter, and then boot.

---

### Post by Coyne on 2005-12-15
Owkey thank you, that worked perfect. But now I still have the problem with the Starting Hotplug,...

---

### Post by 23meg on 2005-12-15
Does hotplug not work for you at all once you skip it? If you remove and reinsert a USB device for example, does it get reactivated?

Anyway, try this options along with pcmcia=no one by one ```
acpi=off
noapic
pci=biosirq
pci=noacpi
```

---

### Post by Coyne on 2005-12-16
Is there a way to permanentaly stop PCMCIA from booting so I don't have to extend the kernel line with pcmcia=no every time??

---

### Post by Coyne on 2005-12-16
Owkey, The noapic command works, now how do I get ubuntu to automatically do the noapic command on boot???

---

### Post by DaMasta on 2005-12-16
Check out his how-to:
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

---

### Post by Coyne on 2005-12-16
Yes, but this doesn't tell me how to disable the apic

---

