---
title: "Mplayer compiling error"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Linux_Noob on 2005-05-05
I followed the guide to compile mplayer posted here "http://www.ubuntuforums.org/showthread.php?t=94" but come to an error. Im not overly sure which lines to paste so I will just paste the last few lines but if i need to post more easily done.

[B]/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1[/B]

Any ideas????

---

### Post by subhankar on 2005-05-05
Try with running ldconfig first and then compiling it.

Regards,
Subhankar

---

### Post by Linux_Noob on 2005-05-05
Idconfig????????

---

### Post by kleeman on 2005-05-05
Actually I had exactly this problem today and I solved it by installing the nvidia-glx-dev package using synaptic. Note I have an nvidia card ;-)

---

