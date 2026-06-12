---
title: "Hotplugging doesn't work in warty"
date: 2005-03-01
forum: Desktop Environments
---

### Post by infornography on 2005-03-01
I wasn't sure what section to post this in, but I'm having trouble with hotplugging on warty. And by trouble, I mean it doesn't work at all.

During thr boot process I get this message:

*Starting hotplug subsystem...
modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-5-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-5-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

Anybody know what this is, or how I can fix it? I would really like to be able to use my flash drive.

Thanks.

---

### Post by doitashimashite on 2005-03-01
I've seen this on several Ubuntu installations so far (including mine).
Doesn't prevent me from mounting flash drives though.
Does your flash drive pop up on your desktop when you connect it?

Also see this link:

[http://www.ubuntuforums.org/showthread.php?t=13143](http://www.ubuntuforums.org/showthread.php?t=13143)

---

### Post by infornography on 2005-03-01
No, it doesn't pop up at all, and I have never actually tried mounting it my self. I guess it would probably work though. It just strikes me as odd because when I installed hoary on this machine the hotplugging worked fine, including the flash drive popping up when I plug it in.

Thanks for the help.

---

### Post by darkoptix on 2005-03-02
Those errors never gave me a problem, allows me to mount my usb key all the time.
There is something on ubuntuguide to get rid if you don't want to see anymore...

---

