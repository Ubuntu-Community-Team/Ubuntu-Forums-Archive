---
title: "Ubuntu refuses to recognize my external monitors"
date: 2014-11-07
forum: Desktop Environments
---

### Post by jpollack on 2014-11-07
Hello all,

I'm running Ubuntu 14.04 as a guest OS using VMWare Fusion 6.  My machine is a MacBook Pro with and Intel Iris Pro graphics chipset, running OSX Yosemite.  I have two external monitors plugged in to the MacBook.  However, Ubuntu only recognizes my main monitor.  When I open up the "Displays" dialog, it only recognizes my main monitor; the other two don't even show up.  Hitting the "detect displays" button does nothing.

I've already read this article, and it didn't help at all :
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2000384](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2000384)

Checking the "Use All Displays in Full Screen" option just mirrors the displays.  Ubuntu still can't recognize the displays and extend the desktop to them.

Any ideas?

---

### Post by phidia on 2014-11-09
I don't know the equivalent in fusion but in but in virtualbox you need to have hardware acceleration enabled which allows the guest OS to use the xorg driver.

---

