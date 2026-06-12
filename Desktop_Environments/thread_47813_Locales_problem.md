---
title: "Locales problem"
date: 2005-07-10
forum: Desktop Environments
---

### Post by Wertigon on 2005-07-10
Hi all, I've got a problem; it seems I've managed to fool Ubuntu into thinking it doesn't have certain locales installed. I get this every time I run make and/or apt-get:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "sv_SE:sv_SV:sv:en_GB:en",
        LC_ALL = (unset),
        LANG = "sv_SE:sv_SV:sv:en_GB:en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

I've tracked the problem down to having something to do with X, somewhere, somehow, messes up my settings, I am unsure of whether it's the X server in itself or GDM however. Anyone knows how I can fix it?

- Per

---

### Post by wrtrdood on 2005-07-12
I had the same problem, albeit with en_US.  Try

sudo dpkg-reconfigure locales

And either select the right locale or regenerate the old one.  I have no idea what may have clobbered mine since it worked fine at one point but running this fixed the problem.

---

