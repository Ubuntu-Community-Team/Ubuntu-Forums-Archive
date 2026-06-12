---
title: "Could not able to install webCam"
date: 2006-12-15
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-12-15
camserv:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed

Hi All.

Please remember the above message. I am trying to install my webCam Veo webcam. I am getting the above message. Please help me to install WebCam.

Thanks in advance.

Swaroop Kunduru.

---

### Post by paparucino on 2006-12-16
> **SwaroopKunduru said:**
> camserv:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed

You need to install a libc6 with a release newer or equal 2.4-1.
Run synaptic then look for libc6 and see what is the latest version and what is the installed version. (for me latest is 2.5.0)
Then from a a terminal run  apt-get install libc6.
If apt-get doesn't find the package may be it is necessary to change the repositories

Hope it helps

---

