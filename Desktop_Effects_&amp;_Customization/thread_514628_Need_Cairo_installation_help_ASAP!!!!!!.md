---
title: "Need Cairo installation help ASAP!!!!!!"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by jayy16 on 2007-07-31
Hi I am new to the whole linux world and I know how to do alot already, I configured Cairo-1.2.6 perfectly and all the build essential stuff is there I followed the tutorial to get Cairo dock but when I put in the make command I get this error ....

cairo-type1-subset.c:368: error: implicit declaration of function 'isspace'
make[3]: *** [cairo-type1-subset.lo] Error 1
make[3]: Leaving directory `/home/jason/Desktop/cairo-1.2.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jason/Desktop/cairo-1.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jason/Desktop/cairo-1.2.6'
make: *** [all] Error 2

anyone know how to fix this?????

---

### Post by Waappu on 2007-08-01
Hi

You can find Cairo-clock from Treviño&#8217;s Ubuntu Repository.

Add correct repo here
[http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)

and type in terminal ```
sudo aptitude install cairo-clock
```

---

### Post by ikak on 2008-02-07
Hey, I have the same error of "implicit declaration..." and i did as you said and entered the command "sudo aptitude install cairo-clock".. cairo-clock installed fine.. no errors.  However, I still get the same error when installing cairo during the "make command"

```
cairo-type1-subset.c:368: error: implicit declaration of function 'isspace'
make[3]: *** [cairo-type1-subset.lo] Error 1
make[3]: Leaving directory `/home/phill/Desktop/cairo-1.2.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/phill/Desktop/cairo-1.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/phill/Desktop/cairo-1.2.6'
make: *** [all] Error 2
```

---

