---
title: "Black screen in Jaunty with ati/radeon"
date: 2009-06-09
forum: General Help
---

### Post by UnicycleBloke on 2009-06-09
Hello,

I have a relatively old PC. The mobo is ASUS P4B533V, and the graphics card is ATI All-In-Wonder Radeon 8500 DV (AGP). My monitor is a new Samsung 2443BW. I'm running on Jaunty.

ATI's fglrx driver does not appear to support the card, but xorg does. I modified my xorg.conf from the default settings, to use the "ati" driver. This mostly works, and I was delighted to have Compiz Fusion to play with, and downloaded Nexuiz 2.5 to give it a go (bit sluggish with my card, but mostly playable). 

I'm experiencing the following problems:

- frequent black screen when booting the PC. The monitor turns
  itself off due to lack of signal, and I have no idea what to
  do next other than reboot and try again. I can of course use
  the xorg.conf recovery tool during booting, but this just re-
  instates the basic defaults.

- if not a black screen on booting, I may get a screen full of 
  garbage, sometimes with what appears to be a corrupted screen 
  dump from the previous session.

- guaranteed black screen when exiting Nexuiz. I don't know if 
  this is related to changing the resolution, but suspect this 
  might be the case.

- occasional black screen when using Compiz add-in for cycling 
  the windows. Not too bothered about the eye candy, but just 
  another indicator of same underlying fault.

I tried downloading the latest ati driver, and followed these instructions [http://www.vanstormbroek.nl/blog/?p=16](http://www.vanstormbroek.nl/blog/?p=16), but that didn't make it better (and possibly worse).

I'd be grateful for any advice on how to proceed.

Incidentally, I'm considering upgrading the graphics card to Sapphire X1650 Pro, which appears to be also fully supported by xorg's ati/radeon driver. I have to have AGP as I'm not ready to fork out for a new mobo and everything. It should have enough power to satisfy my moderate needs, and seems a reasonable compromise option. I'd be interested to know how people are getting on with this card.

Thanks.


UnicycleBloke

---

