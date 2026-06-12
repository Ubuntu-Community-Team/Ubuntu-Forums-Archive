---
title: "Black Screen after Login, 9.04 fresh install"
date: 2009-06-14
forum: General Help
---

### Post by Gauge0123 on 2009-06-14
Hello,
I have recently installed 9.04 by CD on my laptop. Ubuntu was installed fresh over the factory installed Vista. The laptop is a Toshiba Satellite A305-S6905. The specs can be found here:
[http://laptops.toshiba.com/laptops/satellite/A300/A305-S6905](http://laptops.toshiba.com/laptops/satellite/A300/A305-S6905)

The problem is this: following login, the screen will (about 3 out of 4 times) go black. The start up music will still play and I can still manipulate items on my desktop. There is just no image. Does anyone have any advice on how to remedy this? I have the display set to 1280x800 at 60Hz. Any help is appreciated.

---

### Post by jkid on 2009-06-14
when.....you login in press.........alt+ctrl+f4....that will take you to a commande line.....like stuff........login there......and the run  ///sudo dkpg --configure -a ...and see if it worksss.....

---

### Post by Legace on 2009-06-14
Try pressing ALT+F2, login, and type in:
```
metacity --replace
```

Then, press ALT+F7 and see if it works.

I think you are suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/316423](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/316423)

---

### Post by Gauge0123 on 2009-06-20
> Try pressing ALT+F2, login, and type in:
 	Code:
 	metacity --replace 
Then, press ALT+F7 and see if it works.

Yes, this works. But I must do this each time before I login. From having done this, I recalled having read this from earlier:
[http://ubuntuforums.org/showthread.php?p=7488757](http://ubuntuforums.org/showthread.php?p=7488757)

I will try this to see if it works.

---

### Post by Gauge0123 on 2009-06-20
I seems I was wrong. Here
[http://ubuntuforums.org/showthread.php?p=7488757](http://ubuntuforums.org/showthread.php?p=7488757)
it seems the problem was remedied when xorg-driver-fglrx was removed. When I checked to see if it was installed, I found that it wasn't. I am afraid, due to my lack of knowledge on the matter, I wasn't able to follow what was going on in
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/316423](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/316423)
so if anyone has insights into the matter, they will be most appreciated.

Thank you for your help thus far.

---

