---
title: "Everything depends on gstreamer!"
date: 2013-06-24
forum: Desktop Environments
---

### Post by SpecChum on 2013-06-24
I’ve just installed and configured a minimal KDE distro based on the Ubuntu 13.04 minimal CD.  It’s working really well but I have 1 gripe with it.
 
After installing kde-plasma-desktop gstreamer was automatically downloaded as the phonon backend, which as fine as I’d just replace it with my usual vlc backend and remove phonon-backend-gstreamer.
 
So I remove phonon-backend-gstreamer, which gets removed as expected, and I’ve now got autoremove correctly advising me that some gstreamer-* libs are now not required; normal behaviour.  But…autoremove is also recommending that it removes Linux-sound-base, alsa-base etc, some were also included that seemed unrelated to me, such as libsoup.
 
Now I know this is not a major issue, as I don’t _have_ to run autoremove, but it’s just bugging me why this is happening.
 
Why has a gstreamer backend got such a massive dependency list?

---

### Post by dino99 on 2013-06-24
you might ask devs why they are doing cross dependencies everywhere (askubuntu)

---

### Post by SpecChum on 2013-06-24
Good plan.

Done.

---

### Post by mc4man on 2013-06-24
> **SpecChum said:**
> 
 
Why has a gstreamer backend got such a massive dependency list?
It really doesn't have very many dependencies
More a result of how you did your install, minimal + adding..

autoremove just looks for packages marked as automatically installed that have no current  packages installed that depend on them
(I'd gather that a typical 'full' kubuntu install would have kubuntu-desktop installed which would depend on alsa-base

```
apt-cache rdepends alsa-base
alsa-base
Reverse Depends:
  gstreamer1.0-alsa
  xubuntu-desktop
  volumeicon-alsa
  ubuntustudio-desktop
  ubuntu-touch
  ubuntu-gnome-desktop
  lubuntu-core
  kubuntu-desktop
  kubuntu-active
  initramfs-tools-tcos
  flite
  ubuntu-desktop
  linux-sound-base
  libflite1
  gstreamer1.0-alsa
  gstreamer0.10-alsa
  alsa-utils
```
libsoup is used by gnome apps, unity, ect (gnome desktop), run an apt-cache rdepends on.
(apt-cache rdepends libsoup2.4-1

Any packages you believe shouldn't be in the autoremove list just mark as manually installed

---

### Post by SpecChum on 2013-06-24
*slaps head*

Of course, obvious now you mention it, mc4man :)

Thanks for the light bulb!

---

