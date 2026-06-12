---
title: "Error log"
date: 2004-12-05
forum: Desktop Environments
---

### Post by Bannet on 2004-12-05
Ive got a couple of errors on bootup but they go by to fast were do I find the logs.

---

### Post by skabber on 2004-12-05
/var/log/messages is probably what you are looking for.  An easy way to see your boot messages is to type

```
dmesg | more
```

---

### Post by Bannet on 2004-12-05
Thanks I got it.

pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001

Know I just have to figure out this.

Thanks

---

### Post by WW on 2004-12-05
These errors are very common, and harmless:

[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)
[http://ubuntuforums.org/showthread.php?t=6441](http://ubuntuforums.org/showthread.php?t=6441)

---

### Post by Bannet on 2004-12-06
Thank you I got another one

ac97 codec read TIMEOUT [0x5a/0x80c05a]!!!

---

