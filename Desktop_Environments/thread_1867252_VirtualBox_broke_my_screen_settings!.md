---
title: "VirtualBox broke my screen settings!"
date: 2011-10-22
forum: Desktop Environments
---

### Post by tsarv on 2011-10-22
Hello,

I'm running Ubuntu 11.04 with three monitors.  I had trouble installing the virtualbox-ose package through the repositories (I think it was a kernel header issue), so I downloaded the Debian package from the website and installed it.

When I restarted my computer, my monitor settings were messed up.  The image is just mirrored across all three monitors (instead of spanning them) and the screen resolution is 1024*786 instead of 1280*1024.  I can change it back from mirroring using the Monitor Preferences tool.  I can also change two of the monitors back to 1280*1024, but not the third.  I wanted to have a look at the xorg.conf file, but I see that 11.04 no longer uses those.

Any idea what might have happened or how to fix this?

Thanks

---

### Post by tsarv on 2011-10-22
I don't know exactly why this happened but here is how I fixed the screen resolution for the third monitor:

```
xrandr
```

That will list all your monitors.  I found the one that doesn;t have the resolution I wanted.  For me it was called DVI-0.

Then I typed:

```
xrandr --addmode DVI-0 1280x1024

```

Then the 1280x1024 resolution was available in monitor preferences GUI tool.

---

