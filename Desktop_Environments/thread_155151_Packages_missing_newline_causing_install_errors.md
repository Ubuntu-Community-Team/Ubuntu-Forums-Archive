---
title: "Packages missing newline causing install errors"
date: 2006-04-04
forum: Desktop Environments
---

### Post by MattinAK on 2006-04-04
I am trying to install libstdc++5 and to do a general update - but both are failing due to the .deb file missing a newline.  I deleted the package from /var/cache/apt/archives so it would get a new one but it just keeps failing with the same error.  Anyone have any pointers or advice?

Matt

---

### Post by MattinAK on 2006-04-05
Turns out this was a problem with some corrupt files in the VMWare install.  I cleared out the corrupted areas with chkdsk - re-ran the ubuntu installation and all is good now.

Matt

---

