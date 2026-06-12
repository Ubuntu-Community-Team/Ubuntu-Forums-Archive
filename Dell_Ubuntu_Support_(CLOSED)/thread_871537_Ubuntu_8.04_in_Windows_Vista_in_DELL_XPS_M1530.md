---
title: "Ubuntu 8.04 in Windows Vista in DELL XPS M1530"
date: 2008-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by srirajdutt on 2008-07-27
Hello Guys,
 I recently bought a DELL XPS M1530 with the below mentioned configuration. It has got BIOS Version A08 and in default came with windows vista. I ordered an Ubuntu CD and installed the Ubuntu 8.04 LTS Desktop Editon with the feature of Install in Windows. But now I seem to facing various sorts of problems.
The starting sound is very low.
The touchpad doesnt work properly. It seems to be opening randomly something and closing the windows and all sorts of odd things.
Even the nVidia is not working.
I came to know only of these problems so far. If anyone has done the same installation like me please help me out in these problems and tell me what all other things do I need to configure.

Thanks in Advance.

My configuration
DELL XPS M1530
Intel T8300 - core 2 duo 2.4Ghz processor
3GB RAM
250GB HDD
nvidia Ge8600 256mb graphics card

---

### Post by pablopancho on 2008-07-27
Hi,

Problems with touchpad are very common with this laptop. The solution is quite simple in case of normal install (not Wubi) - just simply add "i8042.nomux=1" to the end of kernel line in /boot/grub/menu.lst. The problem is I don't know how different is the windows installation, I mean is there GRUB loader? Can you find menu.lst file?

---

