---
title: "Apt-get update gets fetch error on cdrom"
date: 2010-07-10
forum: Desktop Environments
---

### Post by abigsky on 2010-07-10
I'm getting an error using "sudo apt-get update", it is getting an error trying to fetch a cdrom image.

Error output below:
========================================================
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
========================================================

So what is the syntax for the apt-cdrom? Or is there some other problem?

---

### Post by KdotJ on 2010-07-10
You shouldn't need the CD Rom do perform an apt-get update. Try this, go to Synaptic package manager (System > Administration > Synaptic Package Manager), once it loads, click on "Settings" at the top and choose "Repositories". Once on this page, there should be a tab "Other Sources" (maybe Other Software, I can't remember). On this tab, make sure the CD Rom entry is unchecked.

---

### Post by dmurphy787 on 2010-09-29
That stopped my error but will it stop Ubuntu from getting or using important updates?

---

### Post by drs305 on 2010-09-29
> **dmurphy787 said:**
> That stopped my error but will it stop Ubuntu from getting or using important updates?

No, it just eliminates the CD as a source. And of all the repositories, the CD is likely to have the least up-to-date packages.

---

