---
title: "Kernel compile error in adding new system call can't find standard c library stdio.h"
date: 2009-02-15
forum: General Help
---

### Post by snomula on 2009-02-15
I have successfully compiled new kernel 2.6.24.7. But I am having trouble recompiling the kernel after adding new system call. It is giving me error in detecting standard c libraries as below.

```
arch/x86/kernel/getmyprio.c:1:19: error: stdio.h: No such file or directory
arch/x86/kernel/getmyprio.c:4:26: error: sys/resource.h: No such file or directory
arch/x86/kernel/getmyprio.c:6:25: error: sys/syscall.h: No such file or directory
arch/x86/kernel/getmyprio.c:7:20: error: stdlib.h: No such file or directory

```

I have all the necessary packages installed. I have tried placing my new system call c file in /usr/src/linux/kernel, /usr/src/linux/fs but no luck. Can some one please guide me.

Thanks
S

---

### Post by heindsight on 2009-02-15
You can't use the standard C libraries in kernel code. You'll have to use functions defined in the kernel instead. Have a look at: [http://kernelnewbies.org/FAQ/LibraryFunctionsInKernel](http://kernelnewbies.org/FAQ/LibraryFunctionsInKernel)

---

