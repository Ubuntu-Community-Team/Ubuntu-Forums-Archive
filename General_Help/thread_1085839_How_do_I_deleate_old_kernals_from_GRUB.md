---
title: "How do I deleate old kernals from GRUB?"
date: 2009-03-03
forum: General Help
---

### Post by rsteffens on 2009-03-03
Hi All,

Every time my machine installs a new kernel, the previous ones remain in the GRUB boot loader window.  I'm wondering how to completely remove these old kernels?
Thanks,
Randy

---

### Post by taurus on 2009-03-03
If you want to remove the old kernels from your system, use synaptic.  And if you want to remove the old entries (for old kernels) from /boot/grub/menu.lst, you can edit it and remove them in there.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by fragos on 2009-03-03
Directly editing menu.lst does work but I prefer to use Synaptic to delete unused kernels. It both removes them from my disk and updates menu.lst for me.

---

### Post by 73ckn797 on 2009-03-03
> **fragos said:**
> Directly editing menu.lst does work but I prefer to use Synaptic to delete unused kernels. It both removes them from my disk and updates menu.lst for me.


Thanks! I have wondered about that. Good maintenance measure.

---

### Post by rsteffens on 2009-03-03
Thanks!  I appreciate your help. Is there a way I can automate this?  So that it will automatically delete the old kernel when the new one is installed?

Thanks 
Randy

---

### Post by darco on 2009-03-03
I agree with fragos....
You always want to have a known working kernel in case the new kernel has issues.

darco

---

### Post by Bloch on 2009-03-03
I don't know of any and I don't think it is recommended. A new kernel could break your system if for example it is incompatible with your graphics driver. Loads of people have issues with graphic drivers every time there is a kernel update.

The kernels do seem to accumulate quickly though - I think there are 6 or 7 on my boot screen.

---

### Post by fragos on 2009-03-03
The closest to automation I know about is to configure the number of kernels shown at boot. Older ones wouldn't be deleted but out of sight can be out of mind.

---

### Post by 73ckn797 on 2009-03-04
If a new kernel breaks something then use an older one. If the new kernel works and seems stable after several days to weeks then I will delete the older kernel(s).

---

### Post by rsteffens on 2009-03-05
OK, thanks so much for your help guys!

~Randy

---

