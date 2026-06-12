---
title: "How to install newest kernel?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by sony102600 on 2006-03-03
I have been posting and reading for a while now to get my internet connection up and runnings, and it appears that installing the newest kernel >=2.6.15 will fix my problem?  

Any help in doing so with having a internet connection in windows only?

---

### Post by az on 2006-03-03
[QUOTE=sony102600]I have been posting and reading for a while now to get my internet connection up and runnings, and it appears that installing the newest kernel >=2.6.15 will fix my problem?  

Any help in doing so with having a internet connection in windows only?[/QUOTE]

You may wait a month and upgrade to Dapper.  You can try the flight-4 Dapper install cd right now.  It is more or less stable.

I am not sure how the userspace tools for the 2.6.15 kernel are changed.  I guess you can install the Dapper linux-souce package and compile the kernel for Breezy.  I can't say if it will work, though.  It should.

---

### Post by hw-tph on 2006-03-03
The Dapper kernels are best left for use with Dapper since there are a lot of both userspace and kernel changes between the two. Compiling a new kernel from source isn't a big obstacle - the [Wiki](https://wiki.ubuntu.com/) has some [good pages](https://wiki.ubuntu.com/KernelHowto) on the topic. Keep in mind that you will have to build driver packages as well (if you use nvidia or ATI drivers, or perhaps ndiswrapper).

I applied the archck patchset and built my kernel. ndiswrapper required upgrading ndiswrapper-utils from the Debian unstable repositories but other than that it was smooth sailing. Using gcc 4.0.2 (standard in Ubuntu) was no problem either, much to my surprise.

```
Linux version 2.6.15-archck4.1 (root@devon) (gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)) #1 PREEMPT Fri Feb 24 13:37:07 CET 2006
```


Håkan

---

