---
title: "difference between gnome-core and gnome-desktop-data"
date: 2009-05-25
forum: General Help
---

### Post by agel1 on 2009-05-25
i was trying to install gnome-core in a base installation and this happen
--------------
package gnome-core is not available, but is referred to by another package.
this may mean that the package is missing, has been obsoleted or is only available from another source
however the following packages replace it:
gnome-desktop-data
-----------------

thanks

---

### Post by upbeat.linux on 2009-05-26
The apt error message is saying:

1. some files will be over written
2. package has been replaced (superseded status on launchpad.net)

So, you can simply sudo apt-get install gnome-desktop-data to install (with the changes noted in the release notes for that package) gnome.

See the notes on launchpad.net or packages.ubuntu.com for further info.

---

