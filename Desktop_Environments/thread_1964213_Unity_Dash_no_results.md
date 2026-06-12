---
title: "Unity Dash no results"
date: 2012-04-23
forum: Desktop Environments
---

### Post by paradajz on 2012-04-23
So basically whatever I type into dash, I get no results, except for some music I've been playing in Rhythmbox. I found soultion somewhere to run this:

```
sudo apt-get install --reinstall unity unity-common unity-lens-applications unity-lens-files unity-lens gwibber unity-lens-music unity-place-applications unity-place-files unity-scope-musicstores unity-services unity-2d unity-2d-launcher unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool unity-greeter 
```

However, I get 
E: Unable to locate package unity-lens

error. Any solutions?

EDIT: Sorry, I've selected Lubuntu by accident and can't fix it anymore to Ubuntu.

---

### Post by Krytarik on 2012-04-23
Please see this earlier thread - specifically, try clearing both Zeitgeist's database and Software Center's cache, I'd start with the latter:

[http://ubuntuforums.org/showthread.php?t=1911109](http://ubuntuforums.org/showthread.php?t=1911109)

Regards.

---

