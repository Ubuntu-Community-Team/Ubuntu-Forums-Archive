---
title: "Compiz Broke after upgrade from Hardy to Jaunty"
date: 2009-09-06
forum: Desktop Environments
---

### Post by JustGage on 2009-09-06
**Okay, so upgraded from Hardy to the latest version (Jaunty) which solved a ton of problems BUT, it seemed to break Compiz,**

whenever I would try to enable any effects it would say, "searching for drivers 0%" then fail.

So I did the Compiz check and got this (sort of):
```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```this is actualy what it says **now**, 
but **before**, the line, " Checking for hardware/setup problems... "  said that my graphics card had been backlisted, so I said yes to unbacklisting it because I figured,* hey it worked before it's probably just a false alarm*. 

NOW, when I try to enable compiz in any way, everything on my desktop disappears (windows, top and botom bar) and doesn't come back, 

except for my mouse which I can move and my background,

but keyboard doesn't respond to anything even CTRL+ALT f1-f12, so I'm forced to just pull the plug. 

I've looked around a lot and haven't found an answer, I think it might be related to my **chip being Intel**, but I honestly don't know how to fix this problem. 

Also I looked on my System>Administration>Hardware Drivers and it doesn't list anything, I was wondering if that was normal. 

**is there any way I could *move to the old version ****(of compiz or the driver or whatever)***, because that worked.**

---

### Post by QIII on 2009-09-07
Before you attempt to go back to an older version, take a look here:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Look for the section 

**Performance regressions on Intel graphics cards**

---

### Post by JustGage on 2009-09-08
thanks for the reply I tried to revert it, I honestly can't tell a difference, I'm not sure if it actually changed or not. I would like to point out that it worked in Hardy, I never tried Intrepid, is there a way to go back to Hardy?  

Oh yeah, if it makes any difference, I can't enable 3D chess. just the flat kind.

---

