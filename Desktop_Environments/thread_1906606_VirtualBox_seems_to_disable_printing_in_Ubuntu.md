---
title: "VirtualBox seems to disable printing in Ubuntu"
date: 2012-01-09
forum: Desktop Environments
---

### Post by karlson on 2012-01-09
I am running Maverick on my machine and I have Lexmark X6675 connected to the system via USB.  I also have VirtualBox 4.1 running Windows Vista on the system.  And I have a very interesting situation with Printing.

If I have VirtualBox running with USB device that is my printer enabled to VirtualBox I am unable to print from Ubuntu.  I have to shutdown VirtualBox (I haven't tested but disabling the USB access probably does the same, I'll have to check) and  then I can print from Ubuntu.

Is this normal behavior? Is there a way to configure either VirtualBox or Ubuntu or both so that they can gracefully share the printer?

---

### Post by wyliecoyoteuk on 2012-01-09
Not really, either VB or Ubuntu need to have total control of the USB port.
You could, however, share the printer on one OS and connect to it using the VB networking.

---

### Post by wildmanne39 on 2012-01-09
Hi, > Is this normal behavior? yes it is normal but if you disconnect the usb from within the virtual machine by clicking on it ubuntu should be able to print without shutting down the virtual machine.
Thanks

---

