---
title: "How to get rid of this?"
date: 2005-12-12
forum: General Help
---

### Post by Stormspace on 2005-12-12
> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I get this whenever synaptic runs. Any ideas how to get rid of it?

---

### Post by earobinson on 2005-12-12
that means that those 2 repositorys do not exist remove them, or comment them out, or put in the ubuntu cd rom before you run synaptic each time.

---

### Post by blair on 2005-12-12
As earobinson implied: Note the source: cdrom Synaptic is looking for your CD. When you open your Repositories dialog in Synaptic, you will see a list of data sources. Simply click on the CD source, normally the first item in the list, and click the Delete button.

---

