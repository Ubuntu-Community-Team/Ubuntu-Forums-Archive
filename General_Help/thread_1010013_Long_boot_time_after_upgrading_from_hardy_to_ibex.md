---
title: "Long boot time after upgrading from hardy to ibex"
date: 2008-12-13
forum: General Help
---

### Post by dasistwas on 2008-12-13
Hi,

I just upgraded from hardy to ibex on a mac pro 8 core 2.8Ghz. Booting is now very slow.
I already created dmesg > dmesg.txt and identified the lines, where it is really slow:

```

[   12.919651] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.248791] NET: Registered protocol family 17
[   85.637532] ACPI: WMI: Mapper loaded
[   86.556102] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   86.683667] ppdev: user-space parallel port driver
```

So it's either Registering protocol family 17 that takes so long or ACPI: WMI: Mapper loaded.

Has anyone an idea how to speed up this?

Thanks,
David

---

