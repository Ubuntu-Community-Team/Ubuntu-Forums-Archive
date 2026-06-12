---
title: "Intel video card does not support compiz visual effects"
date: 2010-05-09
forum: Desktop Environments
---

### Post by arvindp3 on 2010-05-09
My desktop has this Intel video card - 

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

This card did not support Compiz visual effects under 9.10. But it worrked under 9.04.   I understand that this was some kind of a bug which was reported on Launchpad (Bug # 492271).  I too logged it and was hoping to see some resolution in Lucid.   I am unable to verify whether this has been fixed in Lucid.  The Lucid LiveCD gave the same problem in demo mode, so I am wondering if it has been resolved in Lucid.  I would go to Lucid only if this has been fixed.

I tried running compiz-check script which reports all "OK" parameters as below.

Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Does anyone know if this has been fixed in Lucid? Or any other information on how to fix this in 9.10, if anything new has been reported.

---

