---
title: "Compiz/Beryl in ATI"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by Narutokun on 2007-09-22
Okay, so I have installed compiz fusion and Beryl on my Sony PCG-K33. My problem is, whenever I try to enable compiz fusion with compiz --replace it gives me:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I have checked on all the tutorials on how to get compiz on ATI and I can't seem to get the drivers for my ATI RADEON IGP 345M. I did try doing the Gnome with XGL but then the screen is all blurry. If I enable the ATI driver in the restricted drivers manager it reboots into a just terminal thing where it says the xserver needs to be reconfigured. Now I can't even see it in the restricted drivers manager.

When I start Beryl in terminal by typing beryl, my toolbars disappear at the top and bottom of the screen and I have to reboot.

I have tried using Envy with manual install which doesn't work because it doesn't detect the ati card. Now I can't even see the ATI driver in the restricted drivers manager.

Can anyone help me? I am really new to Ubuntu so you'll have to give step by step instructions.

---

### Post by Dr Small on 2007-09-22
From what I thought, Beryl and Compiz Fusion don't work on ATI cards, but I could be wrong.

---

### Post by Narutokun on 2007-09-22
Are you sure? I have seen a few tutorials teaching you how to use Compiz Fusion and Beryl on ATI cards.

---

### Post by mysticmatrix on 2007-09-22
> **Narutokun said:**
> Are you sure? I have seen a few tutorials teaching you how to use Compiz Fusion and Beryl on ATI cards.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

---

### Post by Narutokun on 2007-09-22
I followed the link exactly and got this:

* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by joe.turion64x2 on 2007-09-22
If you want to use Compiz or Beryl with an ATI card you'd better try XGL first. It appears to be the only method by which fancy desktop effects (Compiz or Beryl) can be achieved, although there is a myth that open source Radeon driver supports AIXGL as well.

And yes, my laptop's video card is an ATI Radeon Xpress 1100, in which I have been able to enable Beryl using XGL. However I gave up doing it because it is pain setting it up, and almost every update breaks it. On the other hand some hardware problems made me change HD and I have been too lazy to configure it once more.

Good luck.
Joe.

---

### Post by Dark Hornet on 2007-09-22
Hello--I used to have this issue before I said "screw it" and bought an nVidia card for my Ubuntu box--I was able to run beryl for the most part using XGL, however--I did not have any 3D acceleration from my gfx card...so for me it was a trade off, either have 3d acceleration, or beryl.

I didn't like those options, so I just went out and bought a nVidia card, and now I have both compiz and 3D with no issues.....hope this helps, and good luck.

---

### Post by st33med on 2007-09-22
To do it with ATI, do:
```
LIBGL_ALWAYS_INDIRECT=1 compiz(beryl?) --replace --indirect-rendering --ccp &
```

---

### Post by asmoore82 on 2007-09-22
> **joe.turion64x2 said:**
> If you want to use Compiz or Beryl with an ATI card you'd better try XGL first. It appears to be the only method by which fancy desktop effects (Compiz or Beryl) can be achieved, although there is a myth that open source Radeon driver supports AIXGL as well.

And yes, my laptop's video card is an ATI Radeon Xpress 1100, in which I have been able to enable Beryl using XGL. However I gave up doing it because it is pain setting it up, and almost every update breaks it. On the other hand some hardware problems made me change HD and I have been too lazy to configure it once more.

Good luck.
Joe.

+1
but the 8.42 version of the ATI driver promises to add AIGLX/compiz support and is
scheduled to arrive next month(October); I can't wait!!

---

### Post by joe.turion64x2 on 2007-09-22
> **asmoore82 said:**
> +1
but the 8.42 version of the ATI driver promises to add AIGLX/compiz support and is
scheduled to arrive next month(October); I can't wait!!
Is it?

Then October will be an interesting month.

Joe.

---

### Post by Narutokun on 2007-09-23
Thanks for all the replies, I'll try St33m's idea later. I think I have tried XGL but that's what's been making my computer restart into only terminal because it reconfigures xserver?

---

### Post by joe.turion64x2 on 2007-09-23
> **Narutokun said:**
> Thanks for all the replies, I'll try St33m's idea later. I think I have tried XGL but that's what's been making my computer restart into only terminal because it reconfigures xserver?
It is certainly somewhat difficult to make XGL to work (at least with ATI), and it is possible that during the process (specially if it is not properly configured), it kills the X server.

Joe.

---

### Post by Narutokun on 2007-09-23
That may be why I have to keep reconfiguring x server. Well, now I'm downloading the Fiesty Fawn .iso because when I installed ubuntu, I only had the dapper cd. I had to upgrade from dapper to edgy to fiesty fawn. I think after I do a clean install of Fiesty, I will try getting the ATI opensource drivers and then installing Compiz fusion or Beryl.

---

### Post by Lorenz on 2007-09-23
I know how annoying and tiresome it can be to install Compiz or Beryl with an ATI card.
But it does work - once you have the XGL server configured properly and the correct ATI driver is installed it works like a charm. Smooth, quick and looking absolutely stunning. 
Don't give up, try everything you can find and you'll make it work.

---

### Post by Narutokun on 2007-09-23
Thanks for the reasurrance, my brother is helping me now since I found out he got it to work with his ATI card. I'll reformat and install a clean copy of ubuntu 7.04 and try it with the things he's sending me.

---

### Post by Narutokun on 2007-09-24
Sorry for the double post but when I typed in compiz --replace after reinstalling ubuntu 7.04 and following instructions on how to install compiz it gives me this:

/usr/bin/compiz: line 777:  7413 Segmentation fault      (core dumped) $*

Should I try uninstalling and reinstalling compiz?

---

### Post by JJ315 on 2007-10-23
I got the same result trying to run beryl:
Checking for non power of two texture support : failed

btw: Ati radeon Xpress 200 in my PC

---

### Post by JJ315 on 2007-10-23
>  Re: Compiz/Beryl in ATI
I followed the link exactly and got this:

* Beryl system compatibility check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
__________________



I got the same result trying to run beryl:
Checking for non power of two texture support : failed

btw: Ati radeon Xpress 200 in my PC

---

### Post by joe.turion64x2 on 2007-10-23
The new ATI driver is out (8.42) and it supports AIXGL, so there is no further need to be struggling to use XGL now.

---

