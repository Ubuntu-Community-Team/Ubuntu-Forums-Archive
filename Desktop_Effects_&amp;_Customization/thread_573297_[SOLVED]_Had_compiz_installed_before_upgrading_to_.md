---
title: "[SOLVED] Had compiz installed before upgrading to Gutsy, now ccsm broke"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by mooglinux on 2007-10-11
After a numer of headaches getting ccsm to work in Fiesty, i got it to work by using CF Installer-updater. After upgrading to Fiesty, compiz works fine, but ccsm is broken again. I tried using Git4cf but it didnt work. in fact, git4cf didnt seem to do anything, even though i told it to uninstall compiz. Anyway, when i run 'ccsm' in terminal i get the following:

> Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


it looks to me like theres some trouble with python? i dont know. 

Anyway, since compiz was already there i dont see the desktop effects option in my preferances or administation options. So my question is this: is there a way to get the desktop effects that gutsy comes with to appear, and would that allow me to change settings? its essentially the same stuff i have installed, but would it function any better? and how would i fix ccsm without messing with desktop effects (which are the same as the compiz i have installed anyway)

---

### Post by Forlong on 2007-10-11
Please post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by SlugO on 2007-10-11
I installed Compiz Fusion from some repo on Feisty and after upgrading to Gutsy CCSM didn't work for me neither. Apparently the update left Feisty's version of CCSM installed or something. Just go to Synaptic and force the CCSM package to the official Gutsy version, which actually seems to be a bit older than the one I had but atleast it works fine :)

---

### Post by mooglinux on 2007-10-11
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2            Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.1+git20070728~jbs0                Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070926+jbs0               Plugin and configuration tool - Compiz Fusio
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                       Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1            Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3            Settings library for plugins - OpenCompositi
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                       Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings

```


so how would i force ccsm to the gutsy version? find it in synaptic, and reinstall it?

---

### Post by mooglinux on 2007-10-12
Alright, i got it fixed now. i went to synaptic and reinstalled every compiz related package i could find and made sure that there werent any 3rd party repo's enabled, and it workes great now!!

---

### Post by Sturmeh on 2007-10-12
Is gusty going to provide the "latest" compiz-fusion? or the most stable one... :/

---

### Post by Forlong on 2007-10-12
> **Sturmeh said:**
> Is gusty going to provide the "latest" compiz-fusion? or the most stable one... :/
The latest one available (0.6) - no development version of course.

---

### Post by dgrafix on 2007-11-11
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


Im getting the same thing (above) ive tried uninstalling compiz and reinstalling it to no avail :(

---

### Post by Zorael on 2007-11-12
You need to pick the 'completely remove' option in Synaptic. The 'reinstall' one may work as well, not sure. Or do this in a terminal:
```
sudo apt-get **purge** compiz* libcompiz* libdeco* emerald* libemerald*
```

Then reinstall.

This is an issue people with incompatible remnants of Beryl/Compiz in their system face when trying to revert to the official package - meaning upgraders, or people who've dibbled with git source builds and then tried to downgrade back. So you need to make sure you got rid of all the bits and pieces before reinstalling.

If you're trying to get an installation from git sources to work, however, I can't help.

---

### Post by Forlong on 2007-11-12
dgrafix, post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by dgrafix on 2007-11-12
I have solved it now thanks :) I used zorails post and it worked great.

---

