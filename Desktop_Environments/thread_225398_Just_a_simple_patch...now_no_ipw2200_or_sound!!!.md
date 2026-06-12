---
title: "Just a simple patch...now no ipw2200 or sound!!!"
date: 2006-07-29
forum: Desktop Environments
---

### Post by otherside on 2006-07-29
Hello all, I've got a question about a kernel that I just built...  I needed to get the 'PHC' patch into my kernel to enable undervolting of my Pentium M...I used 'make-kpkg --initrd --append-to-version=custom kernel_image kernel_headers modules_image' and followed all the instructions on this site:

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

I used the Dapper kernel source 2.6.15...

Now I don't have any wireless (ipw2200) or sound.  I have tried to extract the firmware (for the ipw2200) to the right /lib/firmware/(kernel rev) location but that doesn't seem to work.  I have tried compiling with the ipw2200 driver built-in and as a module...both the same outcome.  By the way, the PHC patch compiles cleanly and works flawlessly!

Where should I go from here?

Nate

---

### Post by otherside on 2006-07-30
Follow-up...I just tried compiling a vanilla 2.6.16 kernel with the ck12 (Kolivas patch) and the PHC patch...everything compiled perfectly...when I rebooted I still had no wireless but I DID have sound...I just unpacked the ipw2200 2.4 firmware to the /lib/firmware/(kernel rev.) location and rebooted and now the ipw2200 card works fine.  I now have some trouble with an init script that worked fine with the stock Ubuntu kernel...wierd...  Can anyone tell me why the Ubuntu kernel source is buggier than just the vanilla kernel?  I thought that the Ubuntu source has all of the 'official' patches and should make it work better with Dapper?

Nate

---

