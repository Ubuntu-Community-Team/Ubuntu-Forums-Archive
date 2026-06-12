---
title: "Compilation problem"
date: 2009-03-21
forum: General Help
---

### Post by bprof on 2009-03-21
I'm having the following problems compiling a program:

test.c:1:26: error: linux/module.h: No such file or directory
test.c:3:25: error: asm/uaccess.h: No such file or directory
test.c:4:27: error: linux/proc_fs.h: No such file or directory

Here is the head of the program:

#include <linux/module.h>
#include <linux/sched.h>
#include <asm/uaccess.h>
#include <linux/proc_fs.h>

I really appreciate any help in this regards.

Thnx.

---

### Post by HermanAB on 2009-03-21
Is the kernel source installed?  Is /usr/src in the path?

Cheers,

Herman

---

### Post by bprof on 2009-03-21
> **HermanAB said:**
> Is the kernel source installed?  Is /usr/src in the path?

Cheers,

Herman

The /usr/src is in the path, am not sure if the kernel source is installed or not?

Thanks

---

### Post by snova on 2009-03-21
Try installing the **linux-headers** package.

If it still doesn't work, try **linux-headers-generic**.

If it *still* doesn't work, search Synaptic for 'linux-image' to find the particular version you need to match your installed kernel. I'm pretty sure one of the above two will work, though.

---

### Post by bprof on 2009-03-21
> **snova said:**
> Try installing the **linux-headers** package.

If it still doesn't work, try **linux-headers-generic**.

If it *still* doesn't work, search Synaptic for 'linux-image' to find the particular version you need to match your installed kernel. I'm pretty sure one of the above two will work, though.

I've did 

[HTML]uname -a
Linux Desktop 2.6.27-11-generic
[/HTML]

Then I tried all three, but it looks I have them installed.

[HTML]apt-get install linux-headers-2.6.27-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.

apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
[/HTML]

From Synaptic

I found this package installed
Linux kernel image for version 2.6.27 on x86/x86_64 

Is there anything else I need to do/try?

Thnx

---

### Post by bprof on 2009-03-23
Any help please? Is there something missing in what I did?

thx

---

