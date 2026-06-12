---
title: "Regarding kernel modules"
date: 2009-06-09
forum: General Help
---

### Post by dinkyverma279 on 2009-06-09
HI,
 
I have two kernel modules in old linux kernel version 2.6.10. I have to port these .ko modules to kernel version 2.6.27. I have ported it successfully. Since my one of kernel module is using the API of the another kernel modules. I have exported the API made using the EXPORT_SYMBOL and also made that methods extern in header files. I have included that header files in my 2nd modules. 
 
So when I am compiling the first module, it is compiling successully and when i am compiling the 2nd module which is using the API of the first module. It is giving the following errors:
 
WARNING: "Register_Driver" [/usr/src/linux/drivers/usb/my/device/src/a.ko] undefined!
WARNING: "A_Free" [/usr/src/linux/drivers/usb/my/device/src/b.ko] undefined!
 
Can somebody tell the work around for this?  Why these warnings coming even? 
 
regards,
dinky

---

