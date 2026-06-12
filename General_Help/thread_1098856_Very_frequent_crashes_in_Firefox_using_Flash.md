---
title: "Very frequent crashes in Firefox using Flash"
date: 2009-03-17
forum: General Help
---

### Post by Amurko on 2009-03-17
Right now, there's about a 50/50 chance that going to a site with Flash content will cause it to crash.  I'm using the latest Adobe Flash 10 in the repositories.  Running firefox from the terminal yields a "Segmentation Fault" whenever firefox crashes by unexpectedly exiting.

I've tried installing Swiftweasel but it, too, suffers the same problem when visiting Flash Sites.

Tried installing gnash instead but it doesn't load youtube videos (unacceptable)

Tried installing swfdec but it requires you to manually click the flash applet to get it moving (unacceptable)

Tried building gnash from source using apt-build but it won't compile

Tried downloading the latest version of swfdec (version 0.8.4) and its companion mozilla plugin, compiling them, and installing them both but they completely ignore any flash content as if no flash plugin was installed.

I'd like to know how I can get Adobe Flash working properly again so it doesn't crash on every other site.  If that's not possible, then I'd like to be able to get either gnash or swfdec working so that they can provide the basic funcionalities expected from Adobe Flash.  Thanks

---

### Post by D3ath on 2009-03-17
> **Amurko said:**
> Right now, there's about a 50/50 chance that going to a site with Flash content will cause it to crash.  I'm using the latest Adobe Flash 10 in the repositories.  Running firefox from the terminal yields a "Segmentation Fault" whenever firefox crashes by unexpectedly exiting.

I've tried installing Swiftweasel but it, too, suffers the same problem when visiting Flash Sites.

Tried installing gnash instead but it doesn't load youtube videos (unacceptable)

Tried installing swfdec but it requires you to manually click the flash applet to get it moving (unacceptable)

Tried building gnash from source using apt-build but it won't compile

Tried downloading the latest version of swfdec (version 0.8.4) and its companion mozilla plugin, compiling them, and installing them both but they completely ignore any flash content as if no flash plugin was installed.

I'd like to know how I can get Adobe Flash working properly again so it doesn't crash on every other site.  If that's not possible, then I'd like to be able to get either gnash or swfdec working so that they can provide the basic funcionalities expected from Adobe Flash.  Thanks

i used to have some problems with flash. but for about a year now i use:
```
ubuntu-restricted-extras
``` 
it installs everything i need in one package.  Why not try removing flash all together and running that or reinstalling flash. But I'm sure you have reinstalled flash tho.

---

### Post by tenmilez on 2009-03-17
If you run a system monitor try taking a look at your memory. I know my Firefox crashes when I run out of memory (actually run out too, cache will eventually fill up your memory without any problems)

I'm not sure why I run out of memory, but I've **heard** that Firefox allocates memory for flash objects when they're loaded and then it's set until Firefox closes because Firefox has no way of knowing that the flash object has closed.

---

