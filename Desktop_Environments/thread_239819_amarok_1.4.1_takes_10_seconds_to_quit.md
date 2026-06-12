---
title: "amarok 1.4.1 takes 10 seconds to quit?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by thanr01 on 2006-08-19
I installed amarok 1.4.1 via the kubuntu debs (apt-get install amarok). When I quit amarok it takes about 10 seconds to do so everytime... anyone know what's up?

---

### Post by thanr01 on 2006-08-19
I fixed it myself... I had 5223 tracks in my playlist and amarok was set to "Remember current playlist on exit". Unchecking that fixed it. :D

Maybe it's a bug? Well it works excellent now. :cool:

---

### Post by Tresmer on 2006-08-20
> **thanr01 said:**
> I installed amarok 1.4.1 via the kubuntu debs (apt-get install amarok). When I quit amarok it takes about 10 seconds to do so everytime... anyone know what's up?

What is the process for installing via the kubuntu debs?  I would like to try amarok 1.4.1 but (apt-get install amarok) only installs amarok 1.3

Thanks in advance.

---

### Post by thanr01 on 2006-08-20
Well I followed: [http://kubuntu.org/announcements/amarok-1.4.1.php]("http://kubuntu.org/announcements/amarok-1.4.1.php")

Basically add to sources.list, apt-get update then apt-get install amarok should give you the 1.4.1 deb.

---

### Post by Tresmer on 2006-08-22
Thanks!  That worked great.

---

