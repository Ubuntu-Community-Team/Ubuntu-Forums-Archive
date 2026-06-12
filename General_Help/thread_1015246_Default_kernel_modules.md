---
title: "Default kernel modules"
date: 2008-12-18
forum: General Help
---

### Post by Matt Schulte on 2008-12-18
Hi there, I was wondering if someone could point me in the right direction.  I need to know where to go / who to talk to regarding a kernel module that seems to have been enabled in the default Ubuntu kernels dating back to at least Gutsy.

The problem is that someone wrote a driver for _their_ card that uses a common PCI device, just like one of my cards.  They got their driver included in the kernel and somewhere along the way a developer in the Ubuntu community decided that it should be enabled by default.  I would like to refute this idea, because it causes problems with the drivers for other devices in the world.

Who / where should I be to talk about this kind of issue?

Thanks :confused:

---

### Post by swoody on 2008-12-22
Try the ubuntu-devel mailing list:

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

Or you could file a bug report about it. The triagers should be able to foward it to the right place:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

To file a bug you first have to create an account at LaunchPad:

[https://launchpad.net/distros/ubuntu/+bugs/+login](https://launchpad.net/distros/ubuntu/+bugs/+login)

Hope this helps, please let me know if you have any other problems :)

---

