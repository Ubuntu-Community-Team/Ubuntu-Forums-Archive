---
title: "Cannot boot or install ubuntu-session, -desktop. Also cannot suspend"
date: 2015-03-12
forum: Desktop Environments
---

### Post by alan-r-chen on 2015-03-12
So I did the partial upgrade, and it broke my ubuntu gui. I am now using Xfce.
How do I revert it?
Ubuntu 14.04


Also, the other problem.
I cannot sucessfully suspend and desume my computer every time I use it.
Dell E6410

---

### Post by ian-weisser on 2015-03-13
> **alan-r-chen said:**
> So I did the partial upgrade, and it broke my ubuntu gui. I am now using Xfce.
How do I revert it?

You cannot easily revert it. You would have to revert each individual package from the upgrade using dpkg...in the right order.  
The fastest and easiest fix is to back up your data and reinstall.

The most common reason for a 'partial upgrade' is PPA, third-party, or other non-Ubuntu software packages that conflict with the Ubuntu versions.
If you happen to know which software broke your system, please complain to wherever you got it from. They probably did not intend to break your system, and would like to know so they can fix it.
If you don't know how to figure out which software broke your system, then I recommend avoiding PPA, third-party, and other non-Ubuntu packages for now.

---

