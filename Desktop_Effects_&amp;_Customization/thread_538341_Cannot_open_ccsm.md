---
title: "Cannot open ccsm"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by aibradford on 2007-08-29
Can anyone help. 
I just reinstalled compiz but cant open ccsm

here is what i get in terminal:

:~$ ccsm/home/aibradford/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'Traceback (most recent call last):  File "/usr/local/bin/ccsm", line 44, in <module>    idle = ccm.IdleSettingsParser(context)  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 155, in __init__    self.Context.Plugins.items ())  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 154, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 151, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


all of the necessary packages are installed as far as i can tell. desktop-effects is not installed as someone pointed out in a similar thread.

---

### Post by cudaman73 on 2007-08-29
Which repository are you using to install compiz?

---

### Post by aibradford on 2007-08-29
i installed from 
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

from the guide here: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by cudaman73 on 2007-08-29
Did you try following a guide to completely remove compiz and all of it's configs?

If not, you need to, and if so, try it again. I kept missing one package, and it kept me working at compiz for nine hours.

Search the forums for "How to completely remove compiz", and look for one.

Then try a reinstall.

---

