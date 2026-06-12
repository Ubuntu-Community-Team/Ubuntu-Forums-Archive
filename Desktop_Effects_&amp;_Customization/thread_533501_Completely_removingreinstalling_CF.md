---
title: "Completely removing/reinstalling CF"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by umanzor on 2007-08-24
Doesn't matter what I do, I keep getting this error.

> ~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

I've removed, purged, reinstalled, I heard Treviños repos were fine again, but no luck. Nothing is working. How do I completely wipe anything related to CF in my computer so I can start over again?

---

### Post by bigbrovar on 2007-08-24
@ umanzor
   that makes us two

---

### Post by umanzor on 2007-08-24
> **bigbrovar said:**
> @ umanzor
   that makes us two

I did this:

```
sudo apt-get --purge remove compiz* libcompizconfig*
```
```
sudo apt-get --purge remove emerald*
```

Then I removed from my home folder (if you are using GNOME then press ctrl+h to show hidden files):

~/.config/compiz/
~/.emerald/

Then I reinstalled using Treviño's repositories (apparently, I had some extra repositories for CF, maybe I was installing a wrong version).

Now it works, but in order to use emerald I have to run first
```
compiz --replace/CODE]
the
[CODE]emerald --replace
```

---

### Post by bigbrovar on 2007-08-24
try this thread might help   [http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---

### Post by umanzor on 2007-08-24
Also, settings wont change using CCSM, which is bad since I need to disable Sync to VBlank.

---

### Post by bigbrovar on 2007-08-24
yeah was able to reinstall Fusion and it works fine..however nothing i do to ccms changes the setting to my taste..

---

