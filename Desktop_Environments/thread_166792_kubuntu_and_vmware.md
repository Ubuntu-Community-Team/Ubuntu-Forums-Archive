---
title: "kubuntu and vmware"
date: 2006-04-27
forum: Desktop Environments
---

### Post by snowty on 2006-04-27
Hi.
Two days ago I've installed Kubuntu Breezy Badger under VMWare Workstation 5. I added the VMWare Tools and everything worked just fine. I could easily get to my physical harddrive by file sharing. But yesterday, I don't really know why I made a full upgrade in Adept and now the file sharing doesn't work anymore. Is there a package I shouldn't have upgraded?

---

### Post by MartinG on 2006-04-27
Did you re-install Vmware Tools?  If your upgrade included a kernel upgrade, you need to do this .. it's pretty quick and straightforward.

---

### Post by snowty on 2006-04-27
actually I did try to reinstall Vmware Tools but it didn't change anything. If I remember well I read something about having to use the C compiler that was used to compiled the kernel.

---

### Post by MartinG on 2006-04-27
Yes, you need to install gcc-3.4 as well as the other tools in build-essential.  Then run ```
export CC=gcc-3.4
``` just before running the "install tools" script.

---

### Post by snowty on 2006-04-27
Yeah it works!!

Thanks man!!

---

