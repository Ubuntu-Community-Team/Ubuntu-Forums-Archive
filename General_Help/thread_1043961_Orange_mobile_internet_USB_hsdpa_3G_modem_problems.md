---
title: "Orange mobile internet USB hsdpa 3G modem problems"
date: 2009-01-19
forum: General Help
---

### Post by Beazel on 2009-01-19
Hello folks,

Yet another friend has given me an old laptop to install Ubuntu on and this one's proving to be quite the challenge...

His only internet connection is a 3G mobile internet USB dongle (an Option Icon 225) on the Orange network and so far I've not managed to get it working.

I've tried it on two fresh 8.04 installs, once using one "How to" and the next time using another.  I'm about to try it with a fresh 8.10 install (I read somewhere that these things are better supported in Intrepid).  Assuming this time around is a failure would anyone be able to point me in the right direction?  I've exhausted all the "How to"'s I've found so far, and any information would be greatly received!

Many thanks,
Beaz

---

### Post by bumanie on 2009-01-19
Try intrepid, it is better, but not perfect. Not sure whether ndiswrapper will work with a usb modem. As far as wi-fi cards go, if a native linux driver doesn't work or is unavailable, one finds the windows .inf file for the wifi card and installs via ndiswrapper. I have heard of people doing this with wi-fi dongles also. Really have no idea whether it will work with a usb modem dongle, but it's a thought if you find no other way. As far as I know, it is IEEE 802.11 device like a wi-fi card, so ndiswrapper may work if you can find the .inf file somwhere.

---

### Post by TpyKv on 2009-04-16
Hi Beazel,

Have you tried this how to? 

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

works brilliantly :)

---

