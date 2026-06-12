---
title: "problem installing vdrift.."
date: 2008-03-31
forum: Gaming &amp; Leisure
---

### Post by Mia_tech on 2008-03-31
I have download the Vdrift debian files from the ubuntu games site and after installation, they're not showing under games nor respond to the Vdrift command I get command not found
any help appreciated

thanks

---

### Post by Perfect Storm on 2008-03-31
tried with **vdrift** (everything lower case).


otherwise
```
whereis vdrift
locate vdrift
```

---

### Post by Mia_tech on 2008-03-31
I'm posting only part of the output b/c is quite long

```
jorge@ubuntu-box:~$ whereis vdrift
vdrift:
jorge@ubuntu-box:~$ locate vdrift | more
/var/lib/dpkg/info/vdrift-full.md5sums
/var/lib/dpkg/info/vdrift-minimal.list
/var/lib/dpkg/info/vdrift-full.list
/var/lib/dpkg/info/vdrift-minimal.md5sums
/usr/share/games/vdrift
/usr/share/games/vdrift/data
/usr/share/games/vdrift/data/carparts
/usr/share/games/vdrift/data/carparts/tires-rear
/usr/share/games/vdrift/data/carparts/tires-rear/semisim1
/usr/share/games/vdrift/data/carparts/tires-rear/touring1
/usr/share/games/vdrift/data/carparts/tires-rear/lowprofile1
/usr/share/games/vdrift/data/carparts/tires-front
/usr/share/games/vdrift/data/carparts/tires-front/semisim1
/usr/share/games/vdrift/data/carparts/tires-front/touring1
/usr/share/games/vdrift/data/carparts/tires-front/lowprofile1
/usr/share/games/vdrift/data/carparts/brake
/usr/share/games/vdrift/data/carparts/brake/carbon-metallic1
/usr/share/games/vdrift/data/carparts/parts_list
/usr/share/games/vdrift/data/cars
/usr/share/games/vdrift/data/cars/TL2
/usr/share/games/vdrift/data/cars/TL2/TL2.car
/usr/share/games/vdrift/data/cars/TL2/engine.wav
/usr/share/games/vdrift/data/cars/TL2/body.joe
/usr/share/games/vdrift/data/cars/TL2/about.txt
/usr/share/games/vdrift/data/cars/TL2/glass.joe
/usr/share/games/vdrift/data/cars/TL2/wheel_front.joe
/usr/share/games/vdrift/data/cars/TL2/textures
/usr/share/games/vdrift/data/cars/TL2/textures/body04.png
/usr/share/games/vdrift/data/cars/TL2/textures/body01.png
/usr/share/games/vdrift/data/cars/TL2/textures/body00.png
/usr/share/games/vdrift/data/cars/TL2/textures/interior.png
/usr/share/games/vdrift/data/cars/TL2/textures/body.png
/usr/share/games/vdrift/data/cars/TL2/textures/brake.png
/usr/share/games/vdrift/data/cars/TL2/textures/body06.png
/usr/share/games/vdrift/data/cars/TL2/textures/shadow.png
/usr/share/games/vdrift/data/cars/TL2/textures/wheel_front.png
/usr/share/games/vdrift/data/cars/TL2/textures/body05.png
/usr/share/games/vdrift/data/cars/TL2/textures/glass.png
/usr/share/games/vdrift/data/cars/TL2/textures/wheel_rear.png
/usr/share/games/vdrift/data/cars/TL2/textures/body07.png
/usr/share/games/vdrift/data/cars/TL2/textures/body02.png
/usr/share/games/vdrift/data/cars/TL2/textures/body03.png
/usr/share/games/vdrift/data/cars/TL2/wheel_rear.joe
/usr/share/games/vdrift/data/cars/TL2/interior.joe
/usr/share/games/vdrift/data/cars/TL2/collision.joe
/usr/share/games/vdrift/data/cars/MI
/usr/share/games/vdrift/data/cars/MI/license.txt
/usr/share/games/vdrift/data/cars/MI/engine.wav
/usr/share/games/vdrift/data/cars/MI/body.joe
/usr/share/games/vdrift/data/cars/MI/about.txt
/usr/share/games/vdrift/data/cars/MI/glass.joe
/usr/share/games/vdrift/data/cars/MI/MI.car
/usr/share/games/vdrift/data/cars/MI/wheel_front.joe
/usr/share/games/vdrift/data/cars/MI/textures
/usr/share/games/vdrift/data/cars/MI/textures/body00.png
/usr/share/games/vdrift/data/cars/MI/textures/interior.png
/usr/share/games/vdrift/data/cars/MI/textures/body.png
/usr/share/games/vdrift/data/cars/MI/textures/brake.png
/usr/share/games/vdrift/data/cars/MI/textures/shadow.png
/usr/share/games/vdrift/data/cars/MI/textures/wheel_front.png
/usr/share/games/vdrift/data/cars/MI/textures/glass.png
/usr/share/games/vdrift/data/cars/MI/textures/wheel_rear.png
/usr/share/games/vdrift/data/cars/MI/wheel_rear.joe
/usr/share/games/vdrift/data/cars/MI/interior.joe
/usr/share/games/vdrift/data/cars/MI/collision.joe
/usr/share/games/vdrift/data/cars/TC
/usr/share/games/vdrift/data/cars/TC/engine.wav
/usr/share/games/vdrift/data/cars/TC/body.joe
/usr/share/games/vdrift/data/cars/TC/about.txt
/usr/share/games/vdrift/data/cars/TC/glass.joe
/usr/share/games/vdrift/data/cars/TC/wheel_front.joe
/usr/share/games/vdrift/data/cars/TC/textures
/usr/share/games/vdrift/data/cars/TC/textures/body01.png
/usr/share/games/vdrift/data/cars/TC/textures/body00.png
/usr/share/games/vdrift/data/cars/TC/textures/interior.png
/usr/share/games/vdrift/data/cars/TC/textures/body.png
/usr/share/games/vdrift/data/cars/TC/textures/brake.png
/usr/share/games/vdrift/data/cars/TC/textures/shadow.png
/usr/share/games/vdrift/data/cars/TC/textures/wheel_front.png
/usr/share/games/vdrift/data/cars/TC/textures/glass.png
/usr/share/games/vdrift/data/cars/TC/textures/wheel_rear.png
/usr/share/games/vdrift/data/cars/TC/TC.car
/usr/share/games/vdrift/data/cars/TC/wheel_rear.joe
/usr/share/games/vdrift/data/cars/TC/interior.joe
/usr/share/games/vdrift/data/cars/TC/collision.joe
/usr/share/games/vdrift/data/cars/Z06
/usr/share/games/vdrift/data/cars/Z06/engine.wav
/usr/share/games/vdrift/data/cars/Z06/body.joe
/usr/share/games/vdrift/data/cars/Z06/about.txt
/usr/share/games/vdrift/data/cars/Z06/glass.joe
/usr/share/games/vdrift/data/cars/Z06/Z06.car
/usr/share/games/vdrift/data/cars/Z06/wheel_front.joe
/usr/share/games/vdrift/data/cars/Z06/textures
/usr/share/games/vdrift/data/cars/Z06/textures/body01.png
/usr/share/games/vdrift/data/cars/Z06/textures/body00.png
/usr/share/games/vdrift/data/cars/Z06/textures/body.png
/usr/share/games/vdrift/data/cars/Z06/textures/brake.png
/usr/share/games/vdrift/data/cars/Z06/textures/shadow.png
/usr/share/games/vdrift/data/cars/Z06/textures/wheel_front.png
/usr/share/games/vdrift/data/cars/Z06/textures/glass.png
/usr/share/games/vdrift/data/cars/Z06/textures/wheel_rear.png
/usr/share/games/vdrift/data/cars/Z06/wheel_rear.joe
/usr/share/games/vdrift/data/cars/Z06/collision.joe
/usr/share/games/vdrift/data/cars/M3
/usr/share/games/vdrift/data/cars/M3/engine.wav
/usr/share/games/vdrift/data/cars/M3/body.joe
/usr/share/games/vdrift/data/cars/M3/about.txt
/usr/share/games/vdrift/data/cars/M3/glass.joe
/usr/share/games/vdrift/data/cars/M3/M3.car
/usr/share/games/vdrift/data/cars/M3/wheel_front.joe
/usr/share/games/vdrift/data/cars/M3/textures
/usr/share/games/vdrift/data/cars/M3/textures/body01.png
/usr/share/games/vdrift/data/cars/M3/textures/body00.png
/usr/share/games/vdrift/data/cars/M3/textures/interior.png
/usr/share/games/vdrift/data/cars/M3/textures/body.png
/usr/share/games/vdrift/data/cars/M3/textures/brake.png
--More--


```
as shown in the output it seems that is located under /usr/share/games but I browsed there, and I didn't find the executable...any help appreciated

thanks

---

### Post by Perfect Storm on 2008-04-01
you need to find something with /bin/

---

### Post by kaginken on 2008-04-01
Here's a link that should still be aplicable:
[http://ubuntuforums.org/showthread.php?t=632677](http://ubuntuforums.org/showthread.php?t=632677)

Hope that helps!
:guitar:

---

### Post by Mia_tech on 2008-04-01
> **kaginken said:**
> Here's a link that should still be aplicable:
[http://ubuntuforums.org/showthread.php?t=632677](http://ubuntuforums.org/showthread.php?t=632677)

Hope that helps!
:guitar:

thanks finally got it working somehow the deb files, do not install vdrift appropriately

thanks

---

