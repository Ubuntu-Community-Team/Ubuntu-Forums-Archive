---
title: "ccsm won't run"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by reyhan on 2008-03-26
i i just install compiz plugins in this guide [http://ubuntuforums.org/showthread.php?t=659282&page=13]("http://ubuntuforums.org/showthread.php?t=659282&page=13")
when i try to run compiz it won't run this is what happen when i run ccsm on terminal


```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 57, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
    self.Context.Plugins.items ())
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

can someone help me?

---

### Post by lumberjack on 2008-03-26
unfortunately, CCSM has to be run while in an X environment.  Also, i know that CCSM is only an optional manager for the compiz effects.  from my experience with compiz, I'm thinking that you have an unresolved software/hardware issue that's preventing you from running compiz.  I run compiz on an ati card, and have spent quite a bit of time searching forums to resolve issues.  I'll gladly help in any way I can.

---

### Post by lumberjack on 2008-03-26
Oh, and by the way, the text you're getting is normal when ccsm is run in a shell environment.  I'm running compiz right now and got something very similar when i tried running compiz in a text-based environment.

---

### Post by hackerseraph on 2008-04-08
I cant get it to install using the traditional 

sudo apt-get install compizconfig-settings-manager

for some reason today I couldn't find it in the synaptic either. 

Anyone else same issue?

---

### Post by hackerseraph on 2008-04-08
> **hackerseraph said:**
> I cant get it to install using the traditional 

sudo apt-get install compizconfig-settings-manager

for some reason today I couldn't find it in the synaptic either. 

Anyone else same issue?

I think it has been replaced by the **simple ccsm **

---

