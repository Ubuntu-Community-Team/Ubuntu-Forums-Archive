---
title: "Optiplex 755 Boot Failure"
date: 2007-12-18
forum: Dell  Ubuntu Support
---

### Post by cbruner on 2007-12-18
Scenario..

Hardware
[INDENT]Dell Optiplex 755
Intel Quad 2.4
4GB Ram
Intel Video[/INDENT]

Ubuntu 7.10 64bit

Install went fine. Picked up everything. Once install was finished I updated the machine. Since this machine is for work I installed VMware Server from the repository. Everything works great. I shutdown the machine and rebooted for good measure. Everything is fine.

Then over the weekend the power goes out. At the time the machine is off. When I boot the machine now, it gets to about 25% on the splash before it takes me back to the text based boot sequence which is stuck on "Loading Manual Drivers". One press of control-alt-del and I get a login from command line. If I login at this point I am in command line in a "read only" session. In this session all my drives and partitions were available, but my network card was not capable of connecting.

What info could I provide to shed some light on this issue?

Thanks in advance.

---

### Post by forthepeople on 2008-05-14
Maybe the computer is reverting to run-level 1 because something in run level 5 is failing to load. 

Maybe the cause of this is a corrupted system file; maybe this file is the network adapater driver.

Try running fsck on your root file system, but make sure you do umount first.

Actually if you add the -v switch like with most unix commands it should tell you where the error was (if applicable)

---

