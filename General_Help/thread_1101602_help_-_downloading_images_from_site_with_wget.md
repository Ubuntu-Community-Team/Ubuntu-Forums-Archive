---
title: "help - downloading images from site with wget"
date: 2009-03-20
forum: General Help
---

### Post by hazardgreen on 2009-03-20
Hey!

I want to download all .jpg images from a site with wget.
The problem is that the images are hosted elsewhere (all of the the <img src=""> point to different servers)

I've tried adding -H to wget params, but still not working
I used:
wget -r -H -A jpg,jpeg [www.xyz.com](www.xyz.com)


Any idea?:-k

---

### Post by piratebill on 2009-03-20
don't use wget.  I think httrack will do this job better.

---

