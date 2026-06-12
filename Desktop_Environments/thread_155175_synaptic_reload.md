---
title: "synaptic reload"
date: 2006-04-04
forum: Desktop Environments
---

### Post by ELD on 2006-04-04
When pressing the reload button in synaptic i get this:

> 
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)


And this:

> 
W: Duplicate sources.list entry [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages)


How can i stop those errors??

---

### Post by aysiu on 2006-04-04
Go to Applications > Accessories > Terminal and post the output here of these two commands: ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

