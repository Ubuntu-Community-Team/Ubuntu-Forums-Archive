---
title: "Enable 3d Acceleration ATI X300"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by Hyper-x on 2007-03-26
Hello guys, im new with Ubuntu, and want to install XGL and Beryl, I updetad my ATI drivers following this [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")
but my 3d Acceleration is not enabled, how do I enable it??:confused:  Im a Noob in Ubuntu so if you can be very specific.... 
thanks!

---

### Post by adam.tropics on 2007-03-26
Which release  of Ubuntu are you running?...and which part of the guide did you do, method1 or method 2....and your output from a terminal of 
```
fglrxinfo
```

---

### Post by Hyper-x on 2007-03-26
Sure I am running Ubuntu 6.10 I followed the Method 1 and my output is
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

thx

---

### Post by Hyper-x on 2007-03-26
anyone?:confused:

---

### Post by mertle on 2007-03-26
This is a bit of a long shot, since I haven't gotten Beryl to work on my own system yet (at least not with Ubuntu, with Mepis it was a dream). I had a similar problem after I installed fglrx and it using Mesa instead of ATI. Try:

$ sudo depmod -a

Then see if your output still shows Mesa.

- mertle

---

