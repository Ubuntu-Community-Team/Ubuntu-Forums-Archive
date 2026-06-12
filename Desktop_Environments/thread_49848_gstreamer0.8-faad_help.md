---
title: "gstreamer0.8-faad help"
date: 2005-07-18
forum: Desktop Environments
---

### Post by Sephiriz on 2005-07-18
I need support for m4a files on my computer, but I can't seem to install gstreamer0.8-faad. This is the error I get when attempting to do so:
```

gstreamer0.8-faad:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libgstreamer0.8-0 (>=0.8.10-1) but 0.8.9-1ubuntu4 is to be installed

```

I've read that changing libc6 is NOT recommended, and I can't update the lib either because of the same libc6 dependency error.  Is there perhaps an earlier version that I can somehow use?

EDIT:  The solution was to disable the Marillat repositories in /etc/apt/sources.list, after which I could get a working version of gstreamer via a backport.

---

