---
title: "Error..need help to fix"
date: 2006-01-21
forum: Desktop Environments
---

### Post by shafer5 on 2006-01-21
Hey guys I have an error

Code
> E: Type 'eb' is not known on line 30 in source list /etc/apt/sources.list

can someone please tell me how to fix this?

i think it is suppose to be "deb" instead of "eb"

---

### Post by Adrian on 2006-01-21
[QUOTE=shafer5]
i think it is suppose to be "deb" instead of "eb"[/QUOTE]
That sounds probable.

Can you post the entire file so we can take a look?

---

### Post by shafer5 on 2006-01-21
[QUOTE=Adrian]That sounds probable.

Can you post the entire file so we can take a look?[/QUOTE]

ok ok...i got that fixed.

got a new problem:???: 

> W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)



i got this when i tried to install the updates?

are those just files that i have not yet installed on my computer or is it something i should be worried about?

---

### Post by Adrian on 2006-01-22
It seems like you are using obsolete mirrors in your sources.list file. Replace them with working ones and do an **apt-get update**. That means that you will not be able to download packages from those repositories (since they don't exist anymore).

I'm not on my Ubuntu computer right now, so I can't post a working example.
Maybe someone else can?

---

### Post by stalefries on 2006-01-22
You might want to check if your net connection is working, as that can cause problems such as this.

---

### Post by aysiu on 2006-01-22
[QUOTE=shafer5]
i got this when i tried to install the updates?

are those just files that i have not yet installed on my computer or is it something i should be worried about?[/QUOTE] Mirromax is obsolete. See the first link of my signature.

---

