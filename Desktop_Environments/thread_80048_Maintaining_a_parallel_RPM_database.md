---
title: "Maintaining a parallel RPM database"
date: 2005-10-21
forum: Desktop Environments
---

### Post by offby1 on 2005-10-21
Although I have access to alien, so I can install the RPMs manually, our organization packages its products for Redhat 7.3/ES3 only, and thus generates RPMs.  These are not full-on, dependency-managed packages, but are rather the simple kind, and we use an in-house tool to manage dependencies.

Where am I going with this?

I want to have RPM and run it and install these apps freely, independent of the apt database.  Will this work?  If I run rpm to install an RPM that has no dependencies whatsoever, will things just... work?

---

