---
title: "vmware problem"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Megatog615 on 2006-07-25
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

I have to re-run vmware-config.pl every time I restart. Is there a fix for this?

---

### Post by jcrc on 2006-07-25
You don't have to do it everytime you restart.
But, you have to do it every time you install a new kernel.
You have to install the kernel sources.
not sure now what package:
linux-headers or linux-image

best regards
jcrc

---

### Post by Megatog615 on 2006-07-26
> **jcrc said:**
> You don't have to do it everytime you restart.
But, you have to do it every time you install a new kernel.
You have to install the kernel sources.
not sure now what package:
linux-headers or linux-image

best regards
jcrc
I have not installed a new kernel. This happens EVERY time I restart my computer.

---

### Post by jcrc on 2006-07-26
Maybe when you installed vmware you were using a kernel version, and meanwhile you upgraded something and also the kernel version.

When you use the command /usr/bin/vmware-config.pl does vmware works after that?
Or it returns an error saying that the kernel sources are missing?
If so, try so install the packages I told you on the last post, and rerun the command /usr/bin/vmware-config.pl.
Install also if you don't have, the package gcc (c compiler)

when it asks for:
What is the location of the directory of C header files that match your running kernel? 
in my case: /lib/modules/2.6.15-26-686/build/include (kernel 2.6.15-26-686)
in your case: look at dir /lib/modules

I have vmware installed, and the problem you are describing, only happens when I upgrade the kernel.


best regards
jcrc

---

### Post by Megatog615 on 2006-07-27
I'll say it again, *I have not upgraded my kernel since initially installing vmware*. This happens **every** time I reboot my computer, and try to use vmware afterwords.

---

