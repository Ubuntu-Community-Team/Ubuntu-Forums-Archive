---
title: "problems of ATI driver: fglrx"
date: 2006-06-02
forum: Desktop Environments
---

### Post by bsun on 2006-06-02
I followed this page 

  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

and installed fglrx.  But after I reboot, everything looks blured. What happened then?

I really want to fix this because otherwise I need to go back to "vesa".  So please help me and tell me what more information you need. Thanks.

This is the result from "fglrxinfo"

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 SE Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by matoxxx on 2006-06-02
try to install 8.24 driver might help.

---

### Post by bsun on 2006-06-02
Well, originally I installed breezy and everything worked fine. But now .... 

By the way, how to install an 8.24.x version fglrx??  Sorry that I am not an experienced  user of this. 

Thanks.

---

### Post by mattds on 2006-06-02
The fix here worked for me.

[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)

---

### Post by bsun on 2006-06-03
This doesn't work for me. If I replace that libGL.1.2.so, fglrxinfo will give me wrong information like "mesa" stuff and also everything still looks blured.

Also 8.24.8 doesn't work here, possible dapper is using xorg 7.0 and 8.24.8 seems only works for xorg 6.8 or something.

---

