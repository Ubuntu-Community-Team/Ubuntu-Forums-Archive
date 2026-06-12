---
title: "Having newly opened programs centered within primary display of TwinView"
date: 2009-12-13
forum: Desktop Environments
---

### Post by GammaPoint on 2009-12-13
Hi, I just went from having two X sessions to using Twinview for the first time. However, now when I open programs (like OpenOffice) the splash screen is located somewhere at the edge of my primary display (and partly on the other display--my TV). Is there a way to have programs opened within my primary display centered within my primary display?

Thanks,
GP

---

### Post by wojox on 2009-12-13
Only thing I've found:

```
gksudo gedit /etc/openoffice/sofficerc
```

Change the variable Logo to 0 (put 1 again there if you want to re-enable it). That's the only program I have that does that.

---

### Post by GammaPoint on 2009-12-13
> **wojox said:**
> Only thing I've found:

```
gksudo gedit /etc/openoffice/sofficerc
```

Change the variable Logo to 0 (put 1 again there if you want to re-enable it). That's the only program I have that does that.

Well that removes the splash screen rather than centers it, but that's good enough for me. Thanks!

---

