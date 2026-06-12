---
title: "Gnome-language-selector can't install package"
date: 2010-04-05
forum: Desktop Environments
---

### Post by Park7 on 2010-04-05
After a dist-upgrade from Jaunty to Karmic, the gnome-language-selector popped up with an error "*The language support is not installed completely.*" The details box gave the package name "_gnome-user-guide-en_" Further fiddling with the language-selector had me conclude that I could not install this package, so I went to Synaptic.

In Synaptic, I found "_gnome-user-guide-en_" (not installed) and when I tried to install it to satisfy Gnome's needs, another error came up: "*COULD NOT MARK ALL PACKAGES FOR INSTALLATION OR UPGRADE: Package gnome-user-guide-en has no available version, but exists in the database. This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list*"

Note that there IS a similar package that is installed in Synaptic called "_gnome-user-guide_"

I have given some further troubleshooting at the URL below:

[https://answers.launchpad.net/ubuntu/+question/106480](https://answers.launchpad.net/ubuntu/+question/106480)

Any help on this would be really appreciated.

---

### Post by Park7 on 2010-04-05
The package was found in the Universe repository, so enabling Universe fixed my problem. The package installed without a hitch after that.

---

