---
title: "Dependency issues after upgrading from gnome 3.2 to 3.4"
date: 2012-04-20
forum: Desktop Environments
---

### Post by Brizlitman on 2012-04-20
After sudo apt-get install gnome-shell:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnome-shell : Depends: gir1.2-coglpango-1.0 but it is not going to be installed
               Depends: gir1.2-mutter-3.0 (>= 3.3.92) but it is not going to be installed
               Depends: libclutter-1.0-0 (>= 1.9.16) but 1.8.0-1~svn1 is to be installed
               Depends: libcogl-pango0 (>= 1.7.4) but it is not going to be installed
               Depends: libmutter0 (>= 3.4) but it is not going to be installed
               Depends: libmutter0 (< 3.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Brizlitman on 2012-04-20
Never mind..used ppa-purge

---

