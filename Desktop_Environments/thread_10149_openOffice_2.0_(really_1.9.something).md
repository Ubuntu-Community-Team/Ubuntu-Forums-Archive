---
title: "openOffice 2.0 (really 1.9.something)"
date: 2005-01-05
forum: Desktop Environments
---

### Post by mrosenlof on 2005-01-05
Has anybody downloaded the openoffice 2.0 beta software?  It's at  [http://download.openoffice.org/680/index.html](http://download.openoffice.org/680/index.html)

Unfortunately, the download file untars to a bunch of rpm files.  I tried to install them on warty using the 'alien' command necessary for RPMs, but in I try, it didn't run, and I gave up quickly.   Sorry, don't remember what the failure looked like

The OO in the Warty install works just fine, so I had little incentive to dig that night.

I'd still kind of like to try it.  Anybody had better luck?

---

### Post by rwabel on 2005-01-05
yeah I also tried it and without any luck

---

### Post by ra1 on 2005-01-05
You can follow [these]("http://installation.openoffice.org/servlets/ReadMsg?list=dev&msgNo=609") instructions. I tried myself and it works. You only need to replace /opt/openoffice1.9.51 with /opt/openoffice.org1.9.65. And also you will need to make /opt/openoffice.org1.9.65/program/soffice executable 
    ```
sudo chmod +x /opt/openoffice.org1.9.65/program/soffice
```

---

### Post by AndersAA on 2005-01-05
anyone done any performance comparisons with the current stable?  The new one should be waaay faster, as it uses the gtk toolkit instead of it's own custom stuff.

---

