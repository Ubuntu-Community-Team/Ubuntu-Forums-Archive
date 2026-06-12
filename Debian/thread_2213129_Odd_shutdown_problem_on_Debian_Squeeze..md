---
title: "Odd shutdown problem on Debian Squeeze."
date: 2014-03-25
forum: Debian
---

### Post by jwbrase on 2014-03-25
I have a 10-year-old Pentium III machine that I run Debian Squeeze on. I recently switched from the stock 2.6 kernel for squeeze to the backported 3.2 kernel to bring in some drivers for a USB wireless dongle. Since this kernel switch, the machine no longer shuts down or reboots properly. Instead, it gives a single message about an I/O error on fd0 ("end request: I/O error, dev fd0, sector 0"), and then keeps printing similar messages about I/O errors on fd1 (the same "end request" error interspersed with messages about block errors), and seems to hang at that point. After reconfiguring Debian's default magic sysreq settings, using alt+srq+re drops the system to a root shell from which a poweroff or reboot can successfully be performed.

Device files for fd0 and fd1 exist on the system (so the repeated errors on fd1 are because there is no corresponding physical device), but there is only one physical floppy drive (though I had had a second 5.25" drive in the machine back when the thing was using the 2.6 kernel).

Does anybody know what might be causing this? Why does it seem that the system suddenly thinks it cannot reboot unless it can access a non-existent second floppy drive?

---

