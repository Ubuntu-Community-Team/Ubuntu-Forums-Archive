---
title: "Urban Terror running God awfuly slow"
date: 2009-08-13
forum: Gaming &amp; Leisure
---

### Post by sirfenby on 2009-08-13
Alright, so on XP I can run this game maxed out with no problems, Ubuntu.... It runs god awful on low settings.

I have been using Ubuntu for the past 2 days no problems, Tremulous worked just fine maxed out, so I decided to give this a try. I get about 6FPS, I know it ain't network lag because it only occurs if something like frags go off or I step outside, plus my ping is only about 30ms~

I know this is going to be a major factor, I have:
ATI Radeon 1650X Pro
AMD 3200+ 2.4GHz
2.5GB RAM
15GB allocated to the parition running Ubuntu 9.04

anything I need to download?
Oh and keep in mind I am still very new to Ubuntu, so if there is any help you can give me keep it very detailed.

Oh and as a side note, Cube 2 doesn't even start, my screen goes black and thats it, I have to turn the computer off manually and turn it back on.

---

### Post by 569874123 on 2009-08-14
Which method did u use to install these games?
Do u have the latest drivers that support ur graphics card?

---

### Post by Bölvaður on 2009-08-14
> **sirfenby said:**
> anything I need to download?

yes, but you dont go to a website to do it.


Make sure you got any ati driver at all.


Applications &#8594; Accessories &#8594; Terminal
```
glxinfo | grep vendor
```
post the output.

if it doesnt say ATI then go to Systems &#8594; Administration &#8594; Hardware Drivers and select the correct drivers.

---

### Post by sirfenby on 2009-08-14
> **Bölvaður said:**
> yes, but you dont go to a website to do it.


Make sure you got any ati driver at all.


Applications &#8594; Accessories &#8594; Terminal
```
glxinfo | grep vendor
```post the output.

if it doesnt say ATI then go to Systems &#8594; Administration &#8594; Hardware Drivers and select the correct drivers.

I Had already went to the Hardware and Drivers thing, nothing available, but this is the output for that command

fenby@fenby-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

---

### Post by Bölvaður on 2009-08-14
that looks foreign to me.
what is the output of this command

[CODE]lspci | grep VGA
/CODE]

---

### Post by sirfenby on 2009-08-14
> **Bölvaður said:**
> that looks foreign to me.
what is the output of this command

[code]lspci | grep VGA
/CODE]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)

---

### Post by sirfenby on 2009-08-15
> **sirfenby said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)

Justified bump to help with unsolved problem.

---

### Post by sirfenby on 2009-08-15
Nevermind guys, I fixed it with this tutorial
[http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)
I highly recommend it to anybody having ATI problems in 9.04

---

### Post by lisati on 2009-08-15
Good luck

---

### Post by CharmyBee on 2009-08-15
> **sirfenby said:**
> Nevermind guys, I fixed it with this tutorial
[http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)
I highly recommend it to anybody having ATI problems in 9.04

Latest fglrx does not support the non-HD radeons.

---

### Post by sirfenby on 2009-08-15
> **CharmyBee said:**
> Latest fglrx does not support the non-HD radeons.
Are you saying the guide wasn't suppose to work?

---

### Post by CharmyBee on 2009-08-16
> **sirfenby said:**
> Are you saying the guide wasn't suppose to work?

It wouldn't. He is using 9.04. Support for his card was dropped in March 2009. Earlier drivers will not work in 9.04

---

### Post by sirfenby on 2009-08-16
> **CharmyBee said:**
> It wouldn't. He is using 9.04. Support for his card was dropped in March 2009. Earlier drivers will not work in 9.04

But it worked just fine...
Not only do I maintain an FPS of 60+ but it also fixed the timing problems on StepMania.

---

