---
title: "Locked gpac to current version, but still tries to upgrade"
date: 2009-02-06
forum: General Help
---

### Post by Nakor BlueRider on 2009-02-06
Hey all,

The short version is, there seems to be a bug with MP4Box on Intrepid that causes it to segfault.  I found some info on a couple workarounds - first was to install the Hardy version of libgpac0.4.4 which I did, marked it as locked, and that much is now fine - it is locked to its hardy version and isn't bothering me to upgrade.

Now, that didn't solve the problem so I went ahead and followed these steps:

```
#apt-get source gpac
#cd gpac-0.4.4
#nano debian/rules
(edit the "CFLAGS = -Wall -g" line to read "CFLAGS = -D_GNU_SOURCE=1 -D_FORTIFY_SOURCE=0 -Wall -g" and save the file)
#debuild -us -uc -b
#cd ..
#dpkg -i *.deb
```

I had to do a bit more than that actually (install a tonne of dependency packages which I later removed after the process was complete), but the above should sum it up.

This installed gpac again along with libgpac-dev, and this time MP4Box is working fine.  However, package manager wants to upgrade them to a newer version, which I imagine will just put the broken one back on.  I've marked both gpac and libgpac-dev as version locked in Synaptic Package Manager, but the Update Manager is still asking to upgrade these two packages.  I'm guessing because they're not actually versions off the repositories but built right on the PC or some such.

Is there any way I can get Update Manager to ignore updates for those two packages as well?  I mean, I can uncheck them each time there are updates, but it'd be nice to just have them hidden completely for convenience (in part so that when it does pop up, I know it'll be updates I actually want lol).  In the mean time, I have saved the three .deb files the steps I followed created so I should be able to more quickly reinstall them should I slip up and upgrade by mistake.

Thanks much!

---

### Post by Nakor BlueRider on 2009-02-06
Any ideas for this one?

---

### Post by Nakor BlueRider on 2009-02-09
Last call for help I guess.  Looking in short for a way to make a program I built from source not try to upgrade to a "newer" version off the repositories despite being marked as version locked in Synaptic.

---

