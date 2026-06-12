---
title: "Steam Breezy Crashing resolution"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by soulglo83 on 2006-02-02
after several headbusting reinstalls and hours scouring the internet i had yet to see a cure for the most recent wine/steam bug.  an incessant hanging roughly 30 seconds after runtime, and repeating every time it broke out (either thru patience or ctrl+alt+f#'ing to a different tty) roughly 30 seconds later.

after closely monitoring my processor time for roughly 20 minutes and still remaining under 1:40 between wineserver and wine-preloader, id say i may have found a cure, or rather i assembled one, that worked for me.

wine 0.9.6-0 ubuntu breezy, running a ck1 patched vanilla 2.6.15 kernel and 8178 binaries from nvidia.
no hanging, steam is every bit as responsive as it is windows. finally back to cs'ing w/o leaving ubuntu!

be careful, following the following instructions will displace your previous kernel source directory!

following the instructions found here but change every instance of 2.6.14 to 2.6.15 [http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

(modified 2.6.14 to 2.6.15, just change commands, worked identically)

and after booting into my new kernel (which was simple as hell to make, and only took about an hour, most of which was compile time) i installed nvidia-glx from the official nvidia binary on their site.  

Counterstrike runs fast as hell, hotplug works flawlessly, ipod is recognized still, etc. my kernel is newer, seems a little quicker on the boot (?) and overall i would say a big improvement from 2.6.12-10

---

### Post by soulglo83 on 2006-02-02
confirmed working, after 1 1/2 hours of playing last night i didn't experience a single hiccup, to those that steam based games like half life, hl2 and counter strike, and u have tried everything else, this should fix ur problems.  However if ur steam update is freezing @ 26% or u experiencing any problems other than the symptoms stated above, this probably wont fix ur problem, although it is more than likely worth ur time.

---

### Post by Mr_Grieves on 2006-02-05
I can confirm that upgrading to kernel 2.6.15 solves the issue. Thank you!
Updated [http://cslinux.hacka.net](http://cslinux.hacka.net) for easy reference about this problem.

---

### Post by Mr_Grieves on 2006-02-05
Duplicate.

---

