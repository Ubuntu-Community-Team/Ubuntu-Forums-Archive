---
title: "snes9x and cpu"
date: 2006-04-27
forum: Gaming &amp; Leisure
---

### Post by otacan on 2006-04-27
Hello everybody.

when I play with snes9x or visualboyadvacne on my ubuntu 5.10 it use 100% of the cpu:evil:  and I dont know why

I have a P4 2.66 Ghz and a geforce 4 MX with 64 Mo of ram.

Please help. I dont want to reboot to windows every time i want to play....

---

### Post by graigsmith on 2006-04-28
did you install the best kernel for your hardware? ubuntu comes installed default with the 386 kernel. you probably need the 686 one.  search synaptics for linux-686, and install it. if you haven't already. it will speed your whole system up.

---

### Post by otacan on 2006-04-28
Yes I have already instal this kernel as like the nvidia driver and I still have
the same problem: snes9x use 100% of the cpu:neutral: 

Thanks for yours help

---

### Post by DoktorSeven on 2006-04-28
Yeah, it does on mine too, likely because snes9x uses a software renderer to draw everything.

There's an OpenGL snes9x renderer (osnes9x) but it aways fails on me:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  16
  Current serial number in output stream:  18

```

---

### Post by otacan on 2006-04-29
Well I tried osnes9x et I have the same error :evil:

---

### Post by DoktorSeven on 2006-04-29
Not sure what the deal with osnes9x is, as I compiled my own version and still got the same error.  Something isn't right somewhere.  I'm using zsnes for SNES emulation and it works great, OpenGL renderer and all.

VisualBoyAdvance really doesn't have any solution there; it's all software rendering unlike the Windows version, and it's slow.  I got the Windows version running via Wine (had to copy over mfc42.dll into ~/.wine/windows/system32/) but not only was it not much better even using OpenGL mode, but the thing stretched twice as tall as it should and I'd have to resize the window...

---

### Post by graigsmith on 2006-04-29
does zsnes work any better?
try a different videomode.

---

