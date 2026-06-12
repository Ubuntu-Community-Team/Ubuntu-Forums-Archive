---
title: "ATi Proprietary Linux Driver"
date: 2006-08-07
forum: Desktop Environments
---

### Post by srunni on 2006-08-07
Does anyone know if the ATi Proprietary Linux Driver available at their website is fully functional in Ubuntu? Or does it have bugs/errors?

Thanks

---

### Post by Ziox on 2006-08-07
> **srunni said:**
> Does anyone know if the ATi Proprietary Linux Driver available at their website is fully functional in Ubuntu? Or does it have bugs/errors?

Thanks

I know it's not fully functional for everyone...as for bugs/errors, well I'm one of those unfortunate people whos' card isn't supported by that Driver...

so...results may vary..

---

### Post by Anduu on 2006-08-07
I have a Radeon 9600 and ATIs proprietary drive blows...xorg-driver-fglrx from the repos blows it away.

Just my 2 cents...

---

### Post by srunni on 2006-08-08
I see....xorg-driver-fglrx. I will have to remember that. I have an x300, and I have the proprietary driver installed, but I guess I will replace that.

---

### Post by srunni on 2006-08-09
Well, I did some research, and apparently only the proprietary driver supports 3D acceleration. Also, I heard that having multiple X sessions will cause it to crash....is any of this true? (note: this is for the x300 specifically)

Here are two pages I found:
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300)
[http://linux.togaware.com/survivor/ATI_Radeon.html](http://linux.togaware.com/survivor/ATI_Radeon.html)

---

### Post by Anduu on 2006-08-09
> **srunni said:**
> Well, I did some research, and apparently only the proprietary driver supports 3D acceleration. 

That is news to me...I'm stumped :(

---

### Post by dennisharrison on 2006-08-09
the fglrx packages in the repository are an older version of the proprietary drivers from ati.  They both support 3d acceleration.  I don't know about multiple x sessions but I can use multiple desktops if thats any consolation (even though I don't)

as far as I am concerned ati is kind of crappy on support for 3d in linux right now.  I don't know what the REAL problem is... but everything I do with games on linux involving an ati card or either complicated and/or crappy

but at least by using proprietary drivers you will be able to play some stuff ;p

---

### Post by srunni on 2006-08-09
I guess I might just have to stick with dual boot and use Windows to play my games.

---

### Post by jordilin on 2006-08-09
> **srunni said:**
> Well, I did some research, and apparently only the proprietary driver supports 3D acceleration. Also, I heard that having multiple X sessions will cause it to crash....is any of this true? (note: this is for the x300 specifically)

Here are two pages I found:
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300)
[http://linux.togaware.com/survivor/ATI_Radeon.html](http://linux.togaware.com/survivor/ATI_Radeon.html)

I have the generic ati driver and I have 3D support. Just typing
```
glxinfo | grep rendering
```
and I get:
```
direct rendering: Yes
```
and if I'm not wrong, that means 3D support, right?

---

### Post by dennisharrison on 2006-08-09
not entirely sure
are you using the ati driver that comes with xorg?
in glxinfo are you told you have mesa?
 when I was using the default drivers all I could get was software 3d rendering

---

### Post by Ziox on 2006-08-09
> **dennisharrison said:**
> not entirely sure
are you using the ati driver that comes with xorg?
in glxinfo are you told you have mesa?
 when I was using the default drivers all I could get was software 3d rendering

i believe that jordilian does have 3d acceleration enabled, cuz i'm in the same situation as he is (out-of-the-box rendering), and glxinfo doesn't mention MESA anywhere.  Also I tested glxgears, which is really slow w/ out rendering (turned off manually).  And it increased dramatically, when rendering was turned back on.

---

