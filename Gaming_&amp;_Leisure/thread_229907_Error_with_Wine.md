---
title: "Error with Wine"
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by Jaxilian on 2006-08-05
I am using Ubuntu 6.06 and when I am trying click the audio tab in winecfg, I get this:

ALSA lib pcm_mmap.c:363:(snd_pcm_mmap) mmap failed: Invalid aranygument
*** glibc detected *** free(): invalid pointer: 0x7c029878 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

any ideas? ](*,)

---

### Post by Linuturk on 2006-08-05
I'm hitting the same problems. My guess is, WINE doesn't have the correct windows drivers for your audio hardware. I'm going to try to find my windows audio drivers and try installing them like a program.

---

### Post by DoktorSeven on 2006-08-05
Use search, there are a lot of threads about this.  

Usually it's a problem with creating a temporary file in /tmp.  Nothing to do with Windows drivers, which Wine emulates anyway.

---

### Post by pharmd24 on 2006-08-26
I had a similar problem.  I added both sources from Winehq and compiled it on my box, for my box, and it now works just fine.  

I had the install working fine but I updated from the winehq source and it killed my install....

The directions are at the bottem  [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

