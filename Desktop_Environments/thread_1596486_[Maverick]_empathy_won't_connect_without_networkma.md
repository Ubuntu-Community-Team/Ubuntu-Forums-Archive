---
title: "[Maverick] empathy won't connect without networkmanager"
date: 2010-10-14
forum: Desktop Environments
---

### Post by exclesodia on 2010-10-14
hi,

just did a clean install and update to Maverick, and found that empathy won't connect without internet connection managed by networkmanager (I'm using wvdial to connect to the internet since networkmanager doesn't recognize my modem).
it keeps saying 'Offline -- No Network Connection' unless I deactivate and reactivate the account. It's kinda annoying. 
 
for Lucid, there is a simple fix for this condition, [http://ubuntuforums.org/showthread.php?t=1388808](http://ubuntuforums.org/showthread.php?t=1388808)

but now, there is no entry for empathy in gconf-editor after I did the Maverick fresh install. 

is there anybody have the same problem and know the solution?

I can just install pidgin, but I think it is better to not having redundant apps installed.

---

### Post by dev.konverje on 2010-11-27
As noted in [http://osdir.com/ml/ubuntu-telepathy/2010-10/msg00293.html](http://osdir.com/ml/ubuntu-telepathy/2010-10/msg00293.html)

> An update:  Apparently Empathy has switched from using GConf as its
settings storage to GSettings and its corresponding dconf.  On the first
start of Empathy after doing the dist-upgrade, the Empathy settings are
imported once from GConf into dconf, and then GConf is no longer used
for empathy.  Likewise, I imagine that for new 10.10 installs, there
never will be a GConf empathy entry.

As such, you cannot use gconf-editor to change the autoaway setting.
Instead, you must install the package dconf-tools and use dconf-editor,
which works very much like gconf-editor.

search/modify the same key as you would in gconf-editor
```
/apps/empathy/use_conn set to false
```

---

