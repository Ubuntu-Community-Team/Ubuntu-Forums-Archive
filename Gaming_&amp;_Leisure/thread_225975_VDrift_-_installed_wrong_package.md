---
title: "VDrift - installed wrong package"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by william_nbg on 2006-07-30
I wanted to check out the racing game 'vdrift' I'd heard about and not being carefull I downloaded the wrong package - later, I saw there was a special package just for Ubuntu.

The package I installed seemed to install OK, but I'm getting this funny white spaces in the graphics.

How can I purge the old install and install the Ubuntu version??

---

### Post by Ptero-4 on 2006-07-30
```

sudo apt-get remove --purge vdrift (this removes the ubuntu version)
sudo dpkg -P oldvdriftdeb.deb (this purges the old non-ubuntu install)
sudo apt-get install vdrift (this re-installs the ubuntu version of vdrift).

```

---

### Post by william_nbg on 2006-07-30
Thanks!

I'll give it a shot.

Though, the Ubuntu version is a deb you have to download from their website - It's not in the repo'

---

