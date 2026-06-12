---
title: "CUPS Segmentation Faults"
date: 2009-01-03
forum: General Help
---

### Post by sceptre0 on 2009-01-03
I was trying to get printer sharing working with Windows XP, and I seem to have really messed things up.  I was playing around with the CUPS administration and I added an RSS feed of the print jobs just for fun.  Immediately after I added the RSS feed none of the pages would load other than the main page ([http://127.0.0.1:631](http://127.0.0.1:631)).  When I tried to restart the cups server using "sudo /etc/init.d/cupsys restart" I got a segmentation fault.  I tried restoring the original subscription file in /ect/cups/subscriptions.conf and got a segmentation fault.  I booted into a live CD and was able to restore the subscriptions file, but I am still having problems.  I also cannot open synaptic, and when I run "sudo apt-get update" I get a segmentation fault.  I have tried deleting /var/cache/apt/pkgcache.bin and srcpkgcache.bin using the live CD and that did not help.  Anyone have any ideas?

---

