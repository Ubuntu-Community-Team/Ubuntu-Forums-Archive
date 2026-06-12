---
title: "amd64 OS on x86 computer"
date: 2009-02-18
forum: General Help
---

### Post by pawnrocket on 2009-02-18
For some reason dpkg thinks my system is an amd64 computer. I am running on a Core 2 DUO intel 1.8 and trying to install software but it says that i386 arch cannot be installed on my 'amd64" machine. My system isn't an amd64 .. Also I have the generic kernel installed

Ubuntu 8.10 2.6.27-11-generic

> dpkg: error processing software_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:


any takers?

---

### Post by jespdj on 2009-02-18
You have the 64-bit version of Ubuntu installed. The 64-bit version is not just for AMD processors, it's also for 64-bit Intel processors, despite the name "amd64". Your Intel Core 2 Duo is a 64-bit Intel processor.

What software are you trying to install? Isn't there a 64-bit native version of this software available? Isn't it available in the Ubuntu repository, so that you can install it the normal way with Synaptic or apt-get?

If there really is no 64-bit version of the software available, then you can still install the 32-bit (i386) version - 32-bit software also runs on 64-bit Ubuntu. But you might need to have to do more than just install the package; the software might need 32-bit libraries that you'll also have to install.

To force-install a 32-bit package on a 64-bit system, you can do the following. But as I said above, only do this when you really can't find a 64-bit version of the software.
```
sudo dpkg -i --force-architecture software_i386.deb
```

If you tell us what you're trying to install, we can help you find a 64-bit version or give you more information on how to install it.

---

### Post by pawnrocket on 2009-02-18
Thanks but I have already looked for a 64bit and there isn't one. 

And yes I understand 64bit across two chips. I am just surprised because I didn't realize I had installed it until now. 

I will try to force it. 

Thanks...

---

