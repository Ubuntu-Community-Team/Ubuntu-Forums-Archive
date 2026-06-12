---
title: "openoffice is broken"
date: 2009-03-27
forum: General Help
---

### Post by Brian R. on 2009-03-27
Help i did note take any notice when update manager warned me about updating third party software, and when i clicked ok to update openoffice i broke it, it did not install properly, and i had to use Synaptic package manager to uninstall and when i try to reinstall it does not do it properly and gives the following error message.

E:/var/cache/apt/archives/openoffice.org-core_1%
3a3.0.1-7ubuntu1~intrepid1_i386.deb: short read in buffer_copy
(backend dpkg-deb during './usr/lib/openoffice/basic 3.0/program/libxoll.so')

How can i get back to the earlier version?
Thank you.

---

### Post by James_Lochhead on 2009-03-27
You need to completely remove the program in Synaptic.

Then go System > Administration > Software Sources > Third Party Software
and disable the sources that you enabled.

Then simply re-install in Synaptic.

---

### Post by Brian R. on 2009-03-27
Thank you that worked perfectly.

---

