---
title: "CCSM cannot activate under system-&gt;preferences-&gt;appearance-&gt;desktop effects"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by tbuht_1 on 2007-12-23
I had compiz running previously yet it recently just stopped working and I lost all my desktop effects.  So I went to try and setup the effects once again but noticed that under the appearance -> visual effects tab that I cannot enable a setting higher than extra, meaning CCSM can't work.  Every time I click 'custom' the dialog box gets frozen.  Help anyone?

---

### Post by tbuht_1 on 2007-12-23
I also noticed that I selected the 'extra' option under desktop effects and noticed that just about every effect is working except for the compiz cube plugin.  Yet when I select the 'custom' option, it doesn't like to work and reverts to 'none'.  I really hope someone has a solution.

---

### Post by mathenge on 2007-12-23
Can you tell me more about your computer. Specifically, is your graphics card an nvidia card? There are a few posts here that have dealt with this specific problem. I had the same problem on a Dell laptop with an nvidia card and the problem turned out to be an issue between the nvidia driver and the kernel nvidia driver.

---

### Post by tbuht_1 on 2007-12-23
0

---

### Post by tbuht_1 on 2007-12-24
mathenge, thanks for your quick reply. but yea mine is a Dell w/Nvidia as well!
Here are the main specs: Dell Inspiron 1520 Notebook/2 GB DDR2 RAM/Intel Core 2 Duo T7300 (2.0 ghz.)
As for the video card: 256MB nVidia geForce 8600M GT

So do you really think it is the problem with the Nvidia driver because I was thinking maybe I should reinstall Compiz?
__________________

---

### Post by Forlong on 2007-12-26
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by tbuht_1 on 2007-12-26
Here's the output code you wanted:

```

aravind@aravind-laptop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1    OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                  Compiz option code generator
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1    OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.0+git20071008-0ubuntu1    OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1      Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2      Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1      Compiz configuration settings manager
rc  emerald                                    0.3~git20070717-0ubuntu1        Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1      Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3      Settings library for plugins - OpenCompositi
rc  libemeraldengine0                          0.3~git20070717-0ubuntu1        Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1      Compiz configuration system bindings
aravind@aravind-laptop:~$ 


```

---

### Post by tbuht_1 on 2007-12-26
Sorry for all your troubles but I actually figured it out!!!
Turns out that only the cube was having difficulty working (this part took me a while to figure out actually) and it was a problem with the skydome.  I had the wrong file extension  for a skydome image (jpeg instead of png) and all of my Compiz settings were lost. But now I set them back to the original settings and everything works great!    :KS

---

