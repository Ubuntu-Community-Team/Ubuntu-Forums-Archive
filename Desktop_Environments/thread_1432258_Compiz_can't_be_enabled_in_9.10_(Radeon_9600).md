---
title: "Compiz can't be enabled in 9.10 (Radeon 9600)"
date: 2010-03-17
forum: Desktop Environments
---

### Post by DogoDave on 2010-03-17
Ok I have installed compiz-check and ran it and this is the output.

```
 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 AP [Radeon 9600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 
```

As I understand it compiz doesn't support my graphics card in Ubuntu 9.10 although I did have it working fine in the previous 2 version of Ubuntu. 

My question is,...is that command to omit/ignore my card from the blacklist sure to cause problems or are the effects known in my configuration?  

Can I install that ATI catalyst again in Ubuntu 9.10 or will that not make a difference?

Thanks,



Dave

---

### Post by DogoDave on 2010-03-18
Issue resolved

Ran update manager and something in the updates(updated kernel?) took care of my issue.  

compiz-check now states OK on all points.

---

