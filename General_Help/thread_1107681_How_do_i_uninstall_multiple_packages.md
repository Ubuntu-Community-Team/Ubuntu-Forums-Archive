---
title: "How do i uninstall multiple packages?"
date: 2009-03-27
forum: General Help
---

### Post by MAD_JIHAD on 2009-03-27
Ok so what command do i use to uninsatll multiple packages in ubuntu 8.10.

---

### Post by rsambuca on 2009-03-27
The easiest method would be to use Synaptic Package Manager.  Just select each package for removal and click OK.

---

### Post by James_Lochhead on 2009-03-27
You can use the Synaptic package manager to do this. System > Administration > Synaptic Package manager. Mark all you want for uninstallation/complete uninstallation and then hit apply.

In the terminal you simply type:

sudo apt-get remove <package1> <package2> etc

This removes the packages themselves. This:

sudo apt-get autoremove

Removes unnecessary packages installed because the packages you uninstalled above needed them.

---

### Post by mb_webguy on 2009-03-27
When installing packages from the terminal using apt-get, just list all of the packages you want to install separated by a space.  For example, "sudo apt-get install package1 package2 package3".  To uninstall them, just use "remove" instead of "install".

---

### Post by MAD_JIHAD on 2009-03-27
> **James_Lochhead said:**
> You can use the Synaptic package manager to do this. System > Administration > Synaptic Package manager. Mark all you want for uninstallation/complete uninstallation and then hit apply.

In the terminal you simply type:

sudo apt-get remove <package1> <package2> etc

This removes the packages themselves. This:

sudo apt-get autoremove

Removes unnecessary packages installed because the packages you uninstalled above needed them.
Thx allot i had install like 50 packages by accident i think the autoremove will help :D!

---

