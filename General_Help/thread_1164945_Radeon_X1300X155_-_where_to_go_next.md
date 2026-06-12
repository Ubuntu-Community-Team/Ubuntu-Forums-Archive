---
title: "Radeon X1300/X155 - where to go next?"
date: 2009-05-20
forum: General Help
---

### Post by dc2447 on 2009-05-20
I upgraded to jaunty, I have a Radeon X1300/X1550 card outputted to dual displays.

I understand the binary driver from Ati no longer support my card, it's now in legacy mode and indeed X locks when trying to boot.

Using Xorg only, my machine boots but 2D performance (no desktop effects) is awful and I get frequent lockups and artefacts on my screen.

Do I have any options to get a stable machine using this graphics card under jaunty?

> 01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]

---

### Post by skymera on 2009-05-20
Sadly, ATi have moved your card to "legacy" support. Which will affect Jaunty and newer versions.

There is an options source ATi driver built in to Ubuntu. Though i'm not sure how to enable it :O
I think you may need to edit your Xorg.conf

---

### Post by dc2447 on 2009-05-20
Thanks - but I am using the open source driver, it's just unstable and performs badly.

---

### Post by nolliecrooked on 2009-05-20
you can update the opensource driver by following the guide at the bottom of this page;

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

---

### Post by dc2447 on 2009-05-20
> **nolliecrooked said:**
> you can update the opensource driver by following the guide at the bottom of this page;

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon) Cool.

Is this viewed as a good option?

---

### Post by nolliecrooked on 2009-05-20
> **dc2447 said:**
> Cool.

Is this viewed as a good option?

lol, ummmmm nah not really :P

---

### Post by dc2447 on 2009-05-20
> **nolliecrooked said:**
> lol, ummmmm nah not really :P hmm - thanks anyways

Am trying a single display to see if that helps

---

### Post by nolliecrooked on 2009-05-20
> **dc2447 said:**
> hmm - thanks anyways

Am trying a single display to see if that helps

gl

---

### Post by Yellow Pasque on 2009-05-20
Something definitely sounds wrong. With a correct install of the open-source drivers, 2D performance (but not 3D) should be better than with the closed-source drivers.
Make sure you've purged out any fglrx cruft:
```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```
If you installed a Catalyst driver downloaded from ATI/AMD's site:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

At this point, reinstall libgl1-mesa-glx to make sure you're using the correct verion of libGL.so (in the past, I've had fglrx installs leave the proprietary version behind)
```
sudo apt-get --reinstall install libgl1-mesa-glx
```

---

### Post by Makrin on 2009-05-26
You could try the drivers on here.
[HTML]https://launchpad.net/~xorg-edgers/+archive/ppa[/HTML]
Im using the ones from ubuntu x swat and so far they have been stable :-)

---

### Post by blacklocist on 2009-05-27
I had a ATI X1800 and ran Win XP with dual monitors. I loved my setup then got hooked on Linux. To this day I cannot get dual monitors to work on linux with their worthless Catalyst Control Panel and spent hours messing with aticonfig. The final nail in the coffin was then they moved it to legacy. Thanks ATI.

I know you have probably heard this but go Nvidia. I got a Nvidia 8800gt off ebay for $65 dollars and in less then 15 minutes (included download of driver) had dual monitors working perfectly. The best 65 bucks I have spent :)

Wish you luck!

---

### Post by dc2447 on 2009-05-27
> **Temüjin said:**
> Something definitely sounds wrong. With a correct install of the open-source drivers, 2D performance (but not 3D) should be better than with the closed-source drivers.
Make sure you've purged out any fglrx cruft:
```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```
If you installed a Catalyst driver downloaded from ATI/AMD's site:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

At this point, reinstall libgl1-mesa-glx to make sure you're using the correct verion of libGL.so (in the past, I've had fglrx installs leave the proprietary version behind)
```
sudo apt-get --reinstall install libgl1-mesa-glx
```

Thanks - aptitude had nothing to do when purging and I couldn't find any trace of the binary ati driver.

Reinstalling libgl1-mesa-glx - hasn't helped either.  

What happens with a dual screen is that the cursor goes into a large shape, it looks like a greyed out window menu, the machine becomes unresponsive and eventually needs a hard reboot.

Feeling strongly that this is a dual monitor issue

---

### Post by NormanFLinux on 2009-08-03
Install the open source Radeon drivers. And edit your xorg.conf file to comment ATI instead of vesa as the driver that should boot up with Ubuntu. Then enable compiz. It rocks on 9.04!

---

