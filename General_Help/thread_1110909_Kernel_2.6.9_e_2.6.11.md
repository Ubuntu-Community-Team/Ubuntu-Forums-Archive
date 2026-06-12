---
title: "Kernel 2.6.9 e 2.6.11"
date: 2009-03-30
forum: General Help
---

### Post by Shinzon2 on 2009-03-30
Hi! I've an USB Wi-Fi Adaptor that works only with Kernels 2.6.9 e 2.6.11. Is there a list of associations Ubuntu (or other) version - Kernel? (in this way I can use the one that permits me to use my device).

Thanks!!!!

---

### Post by Dejai on 2009-03-30
I would have prefered a model number and some additional information about the card. However I did dig up some old links, I should warn you that these are in no way supported security wise and it would most likely be a bad idea to run these on a production machine, there are probably workarounds for your device. Firstly check out MadWifi and NdisWrapper find more information about these alternatives at both, [http://madwifi.org/](http://madwifi.org/) and [http://ndiswrapper.sourceforge.net/index.html](http://ndiswrapper.sourceforge.net/index.html) compare your device to the list of devices there.:


If all else fails and you know what your doing.. I will not recommend but the link below may shed some insight: 
[http://blog.blackdown.de/2005/06/26/debian-installer-with-kernel-2611/](http://blog.blackdown.de/2005/06/26/debian-installer-with-kernel-2611/)

---

### Post by Shinzon2 on 2009-03-30
Well the device is:

[http://www.conitech.it/conitech/ita/risorse.asp?cod=CN402USB]("http://www.conitech.it/conitech/ita/risorse.asp?cod=CN402USB")

In that page you can find the source code necessary for using it. I followed the contained instruction on (X)Ubuntu 8.10, Fedora 10, Knoppix 6 but when I try to execute "make -f Makefile.26" it reports "Error 2" ( I guess because it works only with kernel 2.6.9 and 2.6.11).

Thanks!

---

