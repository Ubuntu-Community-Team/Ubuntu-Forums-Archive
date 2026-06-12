---
title: "Cant get compiz working on 7.10"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Metaphysical on 2007-10-30
i just upgraded to 7.10, and under system>preferences there is CompizConfig Settings Manager. When i click it though it does nothing.

---

### Post by Zorael on 2007-10-30
No, it won't start by opening the settings manager.

One way is to create a launcher/shortcut, with the command 'compiz --replace'.

Do note that you'll also want to install emerald to get window borders, and if you have an Nvidia card, there's some stuff you may want to add to your xorg.conf, in the Screen section.

```
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    DefaultDepth    24
```

---

### Post by Metaphysical on 2007-10-30
compiz --replace is already set to execute on startup

---

### Post by Zorael on 2007-10-30
Oh, I see, I misinterpreted. You're saying that when you start the settings manager it doesn't open.

Try calling 'ccsm' from a terminal, does it output anything of interest?

---

### Post by Metaphysical on 2007-10-30
this is what i get:
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by Zorael on 2007-10-30
You say you upgraded to 7.10.

Did you have an earlier installation of Compiz(-Fusion) before? Perhaps completely removing and then reinstalling would help.

edit: that is, removing Compiz, not removing the (K/X)Ubuntu installation.

---

### Post by Metaphysical on 2007-10-30
ok, i tried to completely remove compiz and then reinstall it through synaptic. i opened a terminal and typed compiz and i got this :
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:00c0 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Can't load plugin 'imgjpeg' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'imgjpeg'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'text' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'text'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'neg' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'neg'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Can't load plugin 'wall' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'wall'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'snap' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'snap'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'animation' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'animation'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'expo' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'expo'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'resizeinfo' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'resizeinfo'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'workarounds'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ezoom'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'vpswitch'

---

### Post by Zorael on 2007-10-30
Ugh. It still looks like there's some remnants of an older version in there, seeing as it expects to find plugins compiled towards an older version than the one encountered.

You may have already done this through Synaptic, but I'd try this in a terminal:

edit-- Easy way: sudo apt-get remove compiz* libcompiz* emerald libemerald*

Make sure you don't have any weird and unknown repositories, then sudo aptitude update, and then finally install it.

---

