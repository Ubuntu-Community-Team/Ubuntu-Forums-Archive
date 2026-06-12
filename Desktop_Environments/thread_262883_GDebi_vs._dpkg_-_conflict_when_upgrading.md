---
title: "GDebi vs. dpkg - conflict when upgrading"
date: 2006-09-22
forum: Desktop Environments
---

### Post by cronholio on 2006-09-22
I'm not sure if this is a bug. I downloaded Opera 9.02 to replace my existing 9.00 installation. When I open the deb file in GDebi it tells me there is a conflict with the already installed package "opera". However, installing via "dpkg -i" works fine. I guess most novice users would be lost because they don't know (and don't care) about the existence of the command line.

---

### Post by skymt on 2006-09-22
I should also point out that most novice users use Firefox...

And yes, it appears to be a bug in Gdebi. It should work exactly like dpkg -i, but with dependency tracking.

---

