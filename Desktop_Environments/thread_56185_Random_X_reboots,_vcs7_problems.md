---
title: "Random X reboots, vcs7 problems"
date: 2005-08-11
forum: Desktop Environments
---

### Post by web250 on 2005-08-11
I'm getting random reboots of X ever since I installed a new USB mouse.

It happens after the nodes /dev/vcs7 and /dev/vcsa7 get unloaded and reloaded.

This is really bothersome, as I randomly get kicked back to the log-in screen

---

### Post by ions on 2005-08-11
I'm getting random X reboots too.  Nothing newly installed though.  Looking at dmesg seems to place my problem on ACPI.

The first set of agpart lines are from the original boot I believe.  9 lines down you can see the "ACPI: Power Button (FF) [PWRF]" which is what I'm assuming causes the resulting reboot.

```
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
drivers/usb/input/hid-input.c: event field not found
eth0: no IPv6 routers present
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
```

---

