---
title: "Machine not shutting down"
date: 2006-01-27
forum: Desktop Environments
---

### Post by N8MAN1068 on 2006-01-27
I've got an issue where my machine, once told to shut down, will run through the 'Stopping' processes, then sit at Power Downn....and not turn itself off. I have to hold in the power button for it to turn off.

Now, if this was my pc, I wouldn't care, but I loaded it w/ Edubuntu and am giving it away to a pre-school teacher to use in her class.

Anyone got any ideas?

---

### Post by Peter76 on 2006-01-27
This has got something to do with the power management. If you boot, you probably get some errors right at the beginning. Or the boot command has noapic / nolapic in it. If that is true, remove those in the grub menu. Otherwise, go into your bios and set power management to enbabled, but the other power management option to disable. If it still doesn't work, you probably have a very old pc....

---

