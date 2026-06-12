---
title: "Unknown PCI thingy giving errors..."
date: 2006-07-01
forum: Desktop Environments
---

### Post by evil_elman on 2006-07-01
At boot the following can be seen:

```
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
```

It is also written in the kernel log.

LSPCI in a terminal reveals the following (amongst other things):

```

0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
```

What's up with this PCI bridge? Everything seems to be working fine but these   messages are giving me nightmares... :( 

It's a laptop with a 915PM chipset.

---

### Post by evil_elman on 2006-07-02
Bumping here...

Hmmm... Come to think about it... My infrared port is not found either so maybe that one is probably on this PCI bridge which isn't working...

The following can also be seen in the log output:
```
Jul  2 09:16:17 localhost kernel: [17179572.816000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
```

Just entering 'pci=routeirq' accomplishes nothing, though...

---

