---
title: "Remove a Package from Updates List"
date: 2009-10-21
forum: Desktop Environments
---

### Post by Dahaka14 on 2009-10-21
Is there a way to remove a certain package from being checked for updates?  I loathe the new Kile versions from 2.1 and beyond, which are in the software channels, so I would like to keep my 2.0.1 Kile package intact without having to uncheck the box every time I check for system updates.  Call me lazy, but sometimes I run a sudo apt-get update && sudo apt-get upgrade in the terminal without thinking that Kile will be under that update list as well, and then I have to delete all traces of the new Kile since it messes up the tool bars and prefs for any future installed version.  Is this possible?

---

### Post by Dennis N on 2009-10-21
Start Synaptic Package Manager.
Select the package you don't want updated.
Then, from the menus at the top:
Package > Lock Version,  and check the box.

---

### Post by Dahaka14 on 2009-10-21
Thanks a lot!

---

