---
title: "Kernel"
date: 2009-02-06
forum: General Help
---

### Post by sandip26879 on 2009-02-06
:o

Ubuntu ships with generic kernel. Does it mean that it utilizes all range of processors to their maximum capability? Or it just makes Pentium 4 a high speed 80386 ?

---

### Post by snova on 2009-02-06
> **sandip26879 said:**
> Ubuntu ships with generic kernel. Does it mean that it utilizes all range of processors to their maximum capability? Or it just makes Pentium 4 a high speed 80386 ?

Linux will exploit any processor features it can find. Variants do not differ in respect to feature support, I believe.

---

### Post by sandip26879 on 2009-02-07
My home computer is antique P3 866 MHz machine with only 256 mb ram. Ubuntu runs smoothly but little bit slower. Also my new one is ACER ASPIRE 1 which has intel ATOM processor 1.6 GHz with HT support and 1 GB of ram.

I mean to say that since it is running on old P3 processor. It is compiled for backward processors. So while running on ATOM, it might not be utilizing its advanced features, say, SSE3 feature.

---

### Post by Locutus_of_Borg on 2009-02-07
it is likely compiled for IBM compatible, generic x86

which means it will work for most computers, but also means the kernel has many more lines of code not needed that do nothing but take up space and thus takes a bit longer to initialize for a lot of processors.  If you know your specific hardware, you can get the kernel sources and re-compile the kernel to suit your particular architecture and hardware,  it might take you a few times before you can get it to boot, but will result in a more efficient kernel

---

### Post by sandip26879 on 2009-02-07
:p

Thanks to all of you for your suggestions. I was also planning to recompile kernel. But I thought to discuss the matter before proceeding. I will post the results after its done.

---

### Post by beyboo on 2009-02-07
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

This will help...

---

### Post by sandip26879 on 2009-02-07
> **beyboo said:**
> [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

This will help...

;)

I have found another thread for newbie. I am trying it.
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by igknighted on 2009-02-07
The "master kernel thread" is _the_ authority for compiling kernels in Ubuntu.  Not that anything the other thread says is wrong, but I can personally vouch for the MKT and would encourage it over all others.

---

