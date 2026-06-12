---
title: "Compiz Fusion installed, but it doesn't work"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by jtraub on 2007-06-23
Hi!

I have installed Compiz Fusion on machine with Ubuntu Feisty Fawn, ATi X1900. 
I run from terminal compiz --replace (this prints a lot of messages about loaded plugins). Seems to be fine. But no effects :-(. 

Details.
1. ATi fglrx drivers are installed from Ubuntu repository (with help of Manager of Proprietary drivers)
```

mikv@hawk:~/.compizconfig$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6334 (8.34.8)
mikv@hawk:~/.compizconfig$ glxinfo | grep rendering
direct rendering: Yes

```

2. XGL was installed from standart repos. 
3. Compiz fusion installed accroding to instructions [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by tonybaroneee on 2007-07-21
I also have the x1900 and the exact same problems, lol. I really believe our newer card just isn't supported. 

Same thing with Beryl: Unsupported! [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

