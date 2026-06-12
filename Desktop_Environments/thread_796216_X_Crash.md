---
title: "X Crash"
date: 2008-05-16
forum: Desktop Environments
---

### Post by cent on 2008-05-16
The X windowing system keeps crashing when i enter [this]("http://www.blender.org/documentation/245PythonDoc/indices.html") site in Mozilla Firefox. I have Ubuntu Hardy with compiz fusion enabled, but I'm not sure what info i should post.

**Software**
Mozilla Firefox: Mozilla/5.0 (X11; U; Linux i686; nb-NO; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
Not sure what version of Compiz fusion i have

**Hardware:**
Intel Core 2 Quad
Nvidia Ge Force 8600 GTS
Asus p5k SE main board

I found the following entries in the sys log:
```
May 15 22:43:41 (My PC) kernel: [30253.670261] Xorg[5769]: segfault at 0000011b eip b6ed4a70 esp bfbcb770 error 4
May 15 22:44:05 (My PC) pulseaudio[9051]: pid.c: Stale PID file, overwriting.
May 15 22:50:32 (My PC) kernel: [30663.344157] Xorg[8954]: segfault at 0000ff14 eip b6eaf0c5 esp bfe006ec error 4
May 15 22:50:32 (My PC) kernel: [30663.414913] compiz.real[9172]: segfault at 05910001 eip 05910001 esp bfc9b94c error 4
May 15 22:50:43 (My PC) pulseaudio[9518]: pid.c: Stale PID file, overwriting.
May 15 22:58:51 (My PC) kernel: [31161.461374] compiz.real[9620]: segfault at 000006a0 eip 08055a6d esp bfd57210 error 4
May 15 22:59:01 (My PC) pulseaudio[10038]: pid.c: Stale PID file, overwriting.
```I managed to crash the gui tre times (1.. accidental 2. To comfirm and 3. was when i pressed the wrong button). It seams like Xorg crashed first, then Xorg and Compiz and at last only compiz crashed.

---

### Post by cent on 2008-05-17
Anyone? The screen turns black and returns me to the login prompt when i enter the site. It's quite anoying

---

