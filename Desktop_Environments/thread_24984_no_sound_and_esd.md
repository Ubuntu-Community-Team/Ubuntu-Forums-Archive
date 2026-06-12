---
title: "no sound and esd"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Steel3 on 2005-04-08
Hey all,

Been running Hoary development for a while, and I recently did a fresh reinstall.  Previously I was able to follow the directions at the [Ubuntu Wiki](http://www.ubuntulinux.org/wiki/RestrictedFormats) to tell esd to let go of my soundcard when it wasn't using it so other applications could do everything as normal, but after my reinstall I followed the directions as usual and for some reason only the programs that could output to esd could function normally.

Any suggestions?

---

### Post by Jezze on 2005-04-08
I believe I had the same problem and solved it by "sudo killall esd"

---

### Post by c_dog on 2005-04-08
Or just go into the System>Preferences>Sound menu a uncheck 'Enable sound server startup'. This shuts off esd and doesn't touch ALSA, OSS, or JACK

---

