---
title: "ccsm dead after update :(("
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by xaxas on 2007-12-18
After an update 2 days ago my ccsm crashed and i can't reinstall or anything :(

the System->Preferences->Appearance  Extra effects are working perfectly and so is my vidoe card :(

System->Preferences->Appearance Custom Effects does nothing (just keeps the Extra ones) ... and clicking the Preferences button does nothing :(

System->Preferences->CompizConfig Settings Manager is there but does nothing when i click it :((


~Termial~
The **compiz** command freezes there
[http://img86.imageshack.us/img86/3335/screenshotwb2.png](http://img86.imageshack.us/img86/3335/screenshotwb2.png)  
also:
```
xaxas@helios:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

I tryed installing and reinstalling and uninstaling ccsm with the synaptic manager and it's allways the same result :((

I'm new to this and love Ubuntu but can anyone pleaze hep me get my cube and cool effects back :(

---

### Post by mozetti on 2007-12-18
Have you tried this yet?```
sudo aptitude -purge compizconfig-settings-manager
```

If you don't -purge, aptitude just re-uses the package it originally downloaded. When you -purge, it removes it all and you can re-download it. It might not work, but then again it might.

---

### Post by xaxas on 2007-12-18
Unbelievable :((

No effect :(

did the purge ( the  command is without the "-" i'm on gutsy)
```
sudo aptitude purge compizconfig-settings-manager
```
and then i reinstalled it
```
sudo aptitude install compizconfig-settings-manager
```

... both worked but no change :((
ccsm won't fire up and only gives this in terminal
```
xaxas@helios:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

and this freezes like this :((
```
xaxas@helios:~$ compiz config
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'config'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

---

