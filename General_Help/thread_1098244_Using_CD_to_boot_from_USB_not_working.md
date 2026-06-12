---
title: "Using CD to boot from USB not working"
date: 2009-03-16
forum: General Help
---

### Post by fiddler616 on 2009-03-16
Hello,
I want to have Xubuntu on my USB drive, except none of my computers has a BIOS that supports booting from USB.
So I found [this]("http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/") tutorial, and followed it to the letter (with the exception of changing all references to version 8.10 to 8.04--I'm using Hardy).
Booting off the CD works fine--GRUB comes up, etc. But when it goes to boot, I get a HUGE string of error messages. The last few are:
```

[    26.710265] VFS: Cannot open root device "<NULL>" or unkown-block(104,1)
[    26.710333] Please append a correct "root=" boot option; here are the available partitions:
[    26.710420] Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(104,1)

```
How do I solve this?

Thank you.

---

