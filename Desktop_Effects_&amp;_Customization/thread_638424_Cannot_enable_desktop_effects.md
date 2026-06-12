---
title: "Cannot enable desktop effects"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by sevenworth on 2007-12-12
Hi.

I have an ATI Radeon 9550, just installed 7.10, but cannot enable desktop effects. Is this a graphics card driver problem? on the previous version of Ubuntu, I was able to enable the desktop effects perfectly. What has changed in the new release, and how do I fix the problem?

Thanks in advance.

---

### Post by schauerlich on 2007-12-12
Do you have XGL installed? Run ```
sudo apt-get install xserver-xgl
``` then log out and log back in to install it.

This may provide more information: [http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/](http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/)

---

### Post by sevenworth on 2007-12-12
> **EDavidBurg said:**
> Do you have XGL installed? Run ```
sudo apt-get install xserver-xgl
``` then log out and log back in to install it.

This may provide more information: [http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/](http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/)

I'm missing an important ingredient at the moment: an internet connection. I need to get hold of these extra packages and install them manually. any help on this would be appreciated, I'm still really new to Ubuntu.

I have downloaded the latest driver package from ATI. will I need this?

---

### Post by sevenworth on 2007-12-12
Also, seeing as desktop effects worked fine on 7.04, can I not install the required packages off the 7.04 install disc?

---

