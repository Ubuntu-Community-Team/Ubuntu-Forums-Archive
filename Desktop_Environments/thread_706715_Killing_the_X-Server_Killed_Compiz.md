---
title: "Killing the X-Server Killed Compiz"
date: 2008-02-24
forum: Desktop Environments
---

### Post by SpeakerForTheDead on 2008-02-24
Ok, so this is starting to drive me nuts. I'm a new Ubuntu user, and I finally managed to get Compiz, Emerald, and Kiba dock all set up how I like them this weekend (which actually wasn't that bad). The problem is that I had my system lock up and I restarted the X Server. When I logged back in, not only was compiz no longer working... but the menu entry along the lines of System > Preferenced > &#8220;Advanced Desktop Effects Settings&#8221; which I used to configure compiz in the first place was (and remains) completely gone. 

Can anybody offer some kind of advice?

Speaker

---

### Post by SpeakerForTheDead on 2008-02-24
I've been poking around the forum a little more and figured I'd put up some more information (for what it's worth):

[I]walker@walker-laptop:~$ /usr/bin/ccsm 
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'[/I]

And also:

[I]walker@walker-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0429 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/I]

---

