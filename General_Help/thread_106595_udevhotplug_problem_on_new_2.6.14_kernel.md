---
title: "udev/hotplug problem on new 2.6.14 kernel"
date: 2005-12-21
forum: General Help
---

### Post by skridsko on 2005-12-21
Hi,

I have just compiled a new kernel (2.6.14 vanilla), and it's giving problems on the bootup with udev/hotplug. Error messages are as follows:

* udev requires hotplug support, not started.
* Kernel hotplug support not enabled.

I've ensured that these options are enabled in my kernel configuration:

CONFIG_HOTPLUG=y
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_RAMFS=y

Also, /proc/sys/kernel/hotplug is missing (which would explain the previous error messages)

Does anyone have a solution? By the way, my previous kernel was the ubuntu stock 2.6.12-9-386.

---

### Post by utikawa on 2008-04-14
Hi,

This thread is very old but I was facing the same problem today.
The problem was with the network support. It is needed for hotplug.

---

