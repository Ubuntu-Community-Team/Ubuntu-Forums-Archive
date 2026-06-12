---
title: "Error loading OS message"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by kneedragger on 2007-12-01
My cousin gave me his Dell dimensions E510 which works, but only needs a HD. So I bought a new Sata HD plugged it in and went into the bios to set the cd/dvd drive to boot first. I loaded Ubuntu on the HD restarted the computer and set the HD to load first and a " error loading OS" comes up.
No matter what I do I can't get it to load the OS.

Anyone have any ideas that might help?

Thanks

---

### Post by MrFSL on 2007-12-01
```
Anyone have any ideas that might help?
```

Ideas? Sure - 

1) Bad disk drive that you bought or perhaps damaged during install.

2) Bad / unsuccessful installation.

I think the first thing I would do boot from the Installation disk and check the contents of the hard disk to ensure that everything looks installed correctly.

If it does, I would double-check the BIOS settings and that the Hard disk is detected by the BIOS. Lastly I would try to fix the boot loader / MBR. This can be done from the Live CD by opening a terminal and chroot'ing into the hard disk install environment. 

Lastly, I would check for a defected install disk and reinstall.

---

