---
title: "Dell Latitude D505 no SMBus"
date: 2011-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CRAZyBUg on 2011-04-21
Hi,

I am running an old Dell Latitude D505. It got a Intel 82801DB-M ICH4-M Chipset.

While Intel chipset documentation say: Every 82801DB-M got a SMBus, ubuntu isn't finding it using ´lshw´ or ´lspci´. On Windows XP the SMBus is detected and the temp's are working well. 

Is there a way to force detecting the SMBus when it is somehow *hidden*?

If you need dmesg/lshw/lspci output please tell.

Cheers,
Sebastian

---

### Post by CRAZyBUg on 2011-04-22
Ok seems like this script

[http://lm-sensors.org/svn/lm-sensors/trunk/prog/hotplug/unhide_ICH_SMBus](http://lm-sensors.org/svn/lm-sensors/trunk/prog/hotplug/unhide_ICH_SMBus)

is fixing the hidden smbus, by faking it using hotplug pci.

---

### Post by mörgæs on 2011-04-24
Good, please mark the thread 'solved'.

---

