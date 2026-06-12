---
title: "exPerience gtk engine .deb installer?"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by Andreas1 on 2007-09-12
hello,
I am trying to install the experience gtk engine, however not too successful.
first i downloaded the engine from [http://benjamin.sipsolutions.net/Projects/eXperience]("http://benjamin.sipsolutions.net/Projects/eXperience") and tried to compile it, there was an error message saying i was missing two packages. i could not find those packages in synaptic, gave up.
then i found links to a repository and added them to my sources.list, but synaptic says there is an error in the line i added. despite that, in my synaptic list the package was suddenly there, but when i mark it for install it says that it has to uninstall some other packages, the list is quite funny, it contains quite everything that is installed, including nautilus, firefox, gimp, gnome-panel....

one general question - the items displayed in synaptic - is that .deb packages or is there a difference?

---

### Post by hyperair on 2007-09-12
Yeah. It's the same. Basically Synaptic downloads the DEB's from a repository that's found in the /etc/apt/sources.list file, and installs them along with any dependencies they have. Uninstalling a DEB can be done in Synaptic as well.

---

### Post by Andreas1 on 2007-09-20
Now I have it.
I tried the wrong Repository. For me the "experimental" Repository is the right one (I have Feisty).

---

