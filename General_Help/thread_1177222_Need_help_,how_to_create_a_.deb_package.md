---
title: "Need help ,how to create a .deb package??"
date: 2009-06-03
forum: General Help
---

### Post by colau on 2009-06-03
Hi,
Would anyone please tell how to make a .deb package?

---

### Post by regala on 2009-06-03
> **colau said:**
> Hi,
Would anyone please tell how to create .deb package?

this is a long and complex process (not the actual building of the package per se). you need to know what to put in, which packages it should depend on at runtime, and which packages it depend on to build. if it is something big, you may want to split into headers package, libs package, apps package... and so on.

To say it is not straightforward, knowing you just want to build a package is not enough to be able to answer :)

you want to rebuild a package ?
you want to package some software not included in Ubuntu ?

br, mathieu

---

### Post by Kevbert on 2009-06-03
Here's an [COLOR="Red"][article]("http://www.linuxdevices.com/articles/AT8047723203.html")[/COLOR] that may help.

---

### Post by colau on 2009-06-03
Thanks.

---

