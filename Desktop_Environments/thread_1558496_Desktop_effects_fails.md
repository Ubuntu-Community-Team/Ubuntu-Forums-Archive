---
title: "Desktop effects fails"
date: 2010-08-22
forum: Desktop Environments
---

### Post by Jaxilian on 2010-08-22
Hi
Desktop effects fails to activate on my Optiplex sx260 cause my Intel video seems blacklisted. I got message Blacklisted PCI ID 8086:2562 detected when I tried compiz --replace
Does any know how to unblacklist my Intel 845G so I can try Compiz effects?
I tried this:
```
sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz
```

but cannot find any 8086:2562 string in there.
When I run Compiz check everything looks ok.

```
~$ /usr/share/checkbox/scripts/compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

---

### Post by corrytonapple on 2010-08-22
> **cool Cpu said:**
> your computer is faulty !!!!!!!!!!!!!

and the fault is 
Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
What makes you say that?

---

### Post by Jaxilian on 2010-08-22
This is what I can see regarding direct rendering

```
~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20091221 2009Q4 x86/MMX/SSE2
```

---

