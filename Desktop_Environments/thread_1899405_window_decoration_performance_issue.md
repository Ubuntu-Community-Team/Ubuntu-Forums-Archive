---
title: "window decoration performance issue"
date: 2011-12-23
forum: Desktop Environments
---

### Post by Ulty on 2011-12-23
Hello Ubuntu community,
 

 I have got a performance issue since Ubuntu 11.04.
 When I drag a window around the screen it hangs and slows down.  
 This only occurs as long as i have window decoration in Compiz enabled.  
 I'm now on Ubuntu 11.10 and still have this issue.  
 My computer should be fast enough for this,
 

 4x Intel(R) Core(TM)2 Quad CPU Q6700 @ 2.66GHz
 Memory   8192MB
 ATI Technologies Inc RV770 Radeon HD 4870
 

 Does anyone know how I can fix this  ?

---

### Post by Mahkoe on 2011-12-23
My first thought would be to check the "additional drivers" utility, that would be the easiest way to install a better driver for your graphics card. Otherwise, use this site: (the fact that AMD bothers to make a navigable site is another reason why it's better than intel)
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Ulty on 2011-12-24
Updating the driver worked like a charm.  :D 
Finally my windows have buttons again.

Thank you Mahkoe

---

### Post by BC59 on 2011-12-24
> **Mahkoe said:**
> My first thought would be to check the "additional drivers" utility, that would be the easiest way to install a better driver for your graphics card. Otherwise, use this site: (the fact that AMD bothers to make a navigable site is another reason why it's better than intel)
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

These drivers are not for Linux. 
To install the AMD Linux drivers there are 2 easy ways (and a lot more complicated).
Through the application Jockey (search it in dash) or through the application Synaptic (you have to install it through Software Center)
Through Jockey is most recommended. When you open the application you have 2 options, but only the FGLRX graphic driver is working.
If you have problems, open Synaptic and search for FGLRX. Then install the FGLRX graphic driver from there. Reboot to take effect.

---

