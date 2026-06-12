---
title: "no Compiz in latest Jaunty for Lenovo T61"
date: 2009-04-18
forum: Desktop Environments
---

### Post by rolandbreedveld on 2009-04-18
After the today Compiz upgrade for Jauntu, Compiz isn't working anymore because of blacklisting driver:
(row 69 in  /usr/bin/compiz )
T="$T 8086:2a02 " # Intel GM965
after removing this row , I can start compiz by hand, not autoamtiucally after logging in.

I'm using a Lenovo (IBM) T61

The latest time with Jaunty Beta my PC sometimes hangs completely (only mouse is working) also console is not accessible (ctr-alt-f1)
perhaps about this it's blacklisted ?

---

### Post by binbash on 2009-04-18
BEcause there is a bug pending and it is blacklisted.You can unblock it : [http://ubuntuforums.org/showthread.php?t=1129055](http://ubuntuforums.org/showthread.php?t=1129055)

---

### Post by rolandbreedveld on 2009-04-19
yes, I find out that

I removed compiz, it's frustrating :-S that there are always problems with compiz and the populair Intell card GM965 in Lenovo/IBM Notebooks, after some upgrades it's working fine, but after other new Compiz upgrades, we run again into problems.

The compiz guy's should do better testing on populair hardware products, before releasing.

So, for the upcoming time, no Compiz for me :-(

---

