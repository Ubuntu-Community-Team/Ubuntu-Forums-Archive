---
title: "Software Updates Not Working?"
date: 2005-07-26
forum: Desktop Environments
---

### Post by mgbaron on 2005-07-26
Hi,

I just installed Hoary on a desktop and laptop.  When the OS loaded on the desktop there were lots of updates to intall immediately, but on the laptop it says my system is already up to date.  I know this is not true, because it is running Firefox 1.0.2.  Everything else seems to be working fine.

Does anyone know how I can fix this?

Thanks,

Matt

System Details:
Dell Inspiron 600m
1.8 GHz Pentium M
Connected via built in wireless

---

### Post by mgbaron on 2005-07-26
This was the answer that resolved the problem:

"There are several things that can cause this occurance. But the most prevelant would be that the source list on your desktop and laptop are not in sync. Check your /etc/apt/sources.list file on both, compare for any differences and append as needed (assuming they are of couse the same arch)."

This did the trick.  On the laptop version there were several lines commented out.  I'm not sure why this was different on both installs, but I'm certainly glad it is resolved!

---

