---
title: "Using the nitro patchset with Ubuntu"
date: 2005-10-21
forum: Desktop Environments
---

### Post by Zeroedout on 2005-10-21
Does anyone know how to go about compiling the nitro patchet with a kernel for ubuntu. [https://wiki.ubuntu.com/KernelCompileHowto]("https://wiki.ubuntu.com/KernelCompileHowto") seems a little dated. I was going to try it anyway with other instructions on how to compile nitro (In the nitro release notes), however, i was hoping to see if anyone else had any luck and could tell me some tips beforehand (i got a knack for screwing up), or preferably point me to a detailed howto. I found this: [http://www.sepi.be/category/17/blogid/1]("http://www.sepi.be/category/17/blogid/1") and if you read more and go to the release notes ( [http://users.pandora.be/seppe/nitro/2.6.13.2-nitro1/series]("http://users.pandora.be/seppe/nitro/2.6.13.2-nitro1/series") ) it gives you a pretty clear howto for installation. What I want to know is if these instructions apply to ubuntu, or do I need to modify them? Also is the 2.6.13.2 kernel from kernel.org gonna cause any major problems? Oh, and one more thing, i have an ati card, does this mean i will have to recompile fglrx?

edit: just found the latest nitro patches on the gentoo forum, [http://forums.gentoo.org/viewtopic-t-388992-highlight-nitro.html](http://forums.gentoo.org/viewtopic-t-388992-highlight-nitro.html) so same question though, will the instructions from the release notes work with ubuntu as well?

---

### Post by skoal on 2005-10-21
I know people have used the -ck patchset here before, so there shouldn't be much difference here.

Just download the kernel source, unpack it, patch it, then follow this [guide](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=kernel). It should (hopefully) just be that simple.  Have you ever used make-kpkg before? It's really quite powerful and simple.  *No real need to download the kernel source tree from our repos if you know what you're doing with kernel compilations*.  Just grab the source of kernel.org and off you go! weeeeee....

\\//_

---

### Post by Zeroedout on 2005-10-21
hey, thanks so much for the link to the guide, it worked beautifully!!!! The only problem i encountered was after booting the kernel, fglrx 8.18.6 WOULD compile, however, it had a problem loading. To fix this, i needed to patch firegl_public.c (in /lib/modules/fglrx/build_mod/ ) with this code taken right from the gentoo forums: 

```
--- firegl_public.c.orig        2005-08-16 20:13:33.000000000 +0400 
+++ firegl_public.c     2005-09-23 17:25:49.000000000 +0400 
@@ -121,7 +121,7 @@ 
 #endif 
  
 #ifdef __x86_64__ 
-#include "asm/ioctl32.h" 
+#include "linux/ioctl32.h" 
 #if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,2) 
 #include "linux/syscalls.h" 
 #endif 
@@ -1425,7 +1425,7 @@ 
  
 int ATI_API_CALL __ke_verify_area(int type, const void * addr, unsigned long size) 
 { 
-    return verify_area(type, addr, size); 
+    return access_ok(type, addr, size); 
 } 
  
 int ATI_API_CALL __ke_get_pci_device_info(__ke_pci_dev_t* dev, __ke_pci_device_info_t *pinfo)
``` 
Everything else was allright, and i got a a jump of about 7 fps in ut2004 which was well worth it sine i've gone from about 25 fps in ONS-torlan to 32 fps. Perhaps it was the new kernel or a custom cmpiled one or the nitro patchset, whatever it was it worked! Just thought i'de post this incase anyone else was having trouble with the nitro patchset.

---

