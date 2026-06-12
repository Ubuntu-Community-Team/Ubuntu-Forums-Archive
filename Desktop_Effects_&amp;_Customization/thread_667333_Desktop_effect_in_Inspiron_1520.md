---
title: "Desktop effect in Inspiron 1520"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by vvinuv on 2008-01-14
Hi all
I have dell inspiron 1520 laptop with the following specifications.

Intel(R) Core(TM)2Duo Processor T5250-1.5 GHz, 2MB Cache, 667 MHz FSB
2GB (2 X 1024MB) 667MHz Dual Channel DDR2 SDRAM
Integrated Intel(R) Graphics Media Accelerator X3

I have installed ubuntu 7.10 but i could not use desktop effect. Is there any solution?
Thanks
Vinu V

---

### Post by Forlong on 2008-01-14
What's the output of ```
compiz
``` in a terminal?

---

### Post by vvinuv on 2008-01-16
Hi 
Thank u.
When I run compiz I got the following error.

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

Thanks
Vinu V

---

### Post by Forlong on 2008-01-16
Try running Compiz like this: ```
SKIP_CHECKS=yes compiz
```

---

