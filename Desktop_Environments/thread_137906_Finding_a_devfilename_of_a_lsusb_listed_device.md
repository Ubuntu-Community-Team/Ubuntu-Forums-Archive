---
title: "Finding a /dev/filename of a lsusb listed device"
date: 2006-02-28
forum: Desktop Environments
---

### Post by kurtkraut on 2006-02-28
Hi,

The **lsusb** command gives me that:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 008: ID 22b8:4902 Motorola PCS E398 GSM Phone
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

I would like to know the /dev/filename corresponding to the listed divece (E398 Phone) so I can add it in [Gnome Phone Manager]("http://usefulinc.com/software/phonemgr/")

Any suggestions

---

### Post by cwaldbieser on 2006-02-28
[QUOTE=kurtkraut]Hi,

The **lsusb** command gives me that:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 008: ID 22b8:4902 Motorola PCS E398 GSM Phone
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


```

I would like to know the /dev/filename corresponding to the listed divece (E398 Phone) so I can add it in [Gnome Phone Manager]("http://usefulinc.com/software/phonemgr/")

Any suggestions[/QUOTE]

The easiest way is to unplug it, plug it in, and then look at the end of the output from "dmesg".  You will normally see something about a device being created (something like sdb, sdc, sde, sdf, sdg, etc.).

Another way is just to save the output of "ls /dev" to files before and after plugging in the device.  You can "diff" the two outputs to find new devices that were created when the device was plugged in.

---

### Post by RAOF on 2006-03-01
You could write a udev rule (as per [this howto]("http://www.reactivated.net/udevrules.php")) so that your device was always available as /dev/phone, or something.

---

