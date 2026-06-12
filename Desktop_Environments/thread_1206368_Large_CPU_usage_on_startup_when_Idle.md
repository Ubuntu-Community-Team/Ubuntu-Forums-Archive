---
title: "Large CPU usage on startup when Idle"
date: 2009-07-07
forum: Desktop Environments
---

### Post by map7 on 2009-07-07
I've recently installed Ubuntu 904 64bit ext4 on my new computer (E8400 3.0Ghz, 4GB Ram, 64GB SSD).  The problem is lately when I boot my CPU cores are both at about 55% when the computer is idle.

This started to happen after I selected the feature 'Automatically remember running applications when logging out'.  I turned this feature off but the feature keeps working even though it's off.  Every time I login all my applications load up from the day I turned on the feature.  So somehow this feature has stuck on and I think that is the problem but I cannot find out how to turn it off.

---

### Post by map7 on 2009-07-08
I've worked this out.

It was the Remote Desktop Server trying to run twice.  I found it was in the StartUp applications so I removed it from there, disabled it from the setup and relogged in and the problem has gone away.

---

### Post by Terry Zhou on 2009-07-13
Thanks for the solution, I have got the same issue, resolve it after disable remote desktop.

---

