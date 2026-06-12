---
title: "deb installation under jaunty"
date: 2009-05-03
forum: General Help
---

### Post by poodpood on 2009-05-03
Hi, what does "Error: Dependency is not satisfiable: libgnome2.0-cil (>= 2.16.0)" mean?

I get this when I try to install a .deb package under jaunty, the same package works ok on intrepid.

---

### Post by spiderbatdad on 2009-05-03
you can sometimes contact the package maintainer and request a repair. If you provide a link to the deb package, it might make it easier for someone to help you here.
The message means the package isnt finding a library it needs. In jaunty the lib is called libgnome2-0, not libgnome2.0-cil.
Look for the deb package in the repos, if the problem exists with a package there, it can be reported as a bug, perhaps it still can, as some binary compatibility seems to have been broken, if the same package worked in intrepid.

---

