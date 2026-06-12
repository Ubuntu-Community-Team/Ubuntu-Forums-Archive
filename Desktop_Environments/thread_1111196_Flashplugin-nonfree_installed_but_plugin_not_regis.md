---
title: "Flashplugin-nonfree installed but plugin not registered with FF"
date: 2009-03-30
forum: Desktop Environments
---

### Post by SilvaRizla on 2009-03-30
Hi,

I have installed Flash using the package manager on amd64 but the plugin is not listed in FF about:plugins - How can I register the plugin?

---

### Post by Lunx on 2009-03-30
> **SilvaRizla said:**
> Hi,

I have installed Flash using the package manager on amd64 but the plugin is not listed in FF about:plugins - How can I register the plugin?

And restarting FF doesn't work? I had same problem when I first intalled it on Opera, a quick restart and Opera could then see it.

---

### Post by pjalegria on 2009-03-30
I have the same problem with java on FF3...

---

### Post by SilvaRizla on 2009-03-30
That didn't work although I have now found the fix for anyone else who sees this:  [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)

Turns out I had to copy a .so file from the original .tar.gz package and set the link to it on nspluginwrapper

Thanks anyway

---

### Post by Lunx on 2009-03-30
> **SilvaRizla said:**
> That didn't work although I have now found the fix for anyone else who sees this:  [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)

Turns out I had to copy a .so file from the original .tar.gz package and set the link to it on nspluginwrapper

Thanks anyway

Glad you got it solved anyhow :)

You got me to wondering whether it shows up in my FF installation because I just did a fresh install of Jaunty a couple of hours ago and downloaded it along with a few browser plugins for audio. All of them showed up in FF, so not sure what caused the drama on your system.

---

