---
title: "error in compilation"
date: 2009-04-29
forum: General Help
---

### Post by spiceoflife on 2009-04-29
Hello,
I'm trying to compile the ti_usb_3410_5052.c in order to install an usb driver .but when i compile the module,i got this:


In file included from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /home/zina/Bureau/newnewnew/ti_usb_2.6-1.0/src/ti_usb_3410_5052.c:75:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /home/zina/Bureau/newnewnew/ti_usb_2.6-1.0/src/ti_usb_3410_5052.c:75:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
/home/zina/Bureau/newnewnew/ti_usb_2.6-1.0/src/ti_usb_3410_5052.c:86:27: error: asm/semaphore.h: No such file or directory

So, please is there anybody can help me???

---

