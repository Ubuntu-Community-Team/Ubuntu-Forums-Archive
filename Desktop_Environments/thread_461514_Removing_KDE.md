---
title: "Removing KDE"
date: 2007-06-01
forum: Desktop Environments
---

### Post by bobshowrocks on 2007-06-01
I Installed KDE, and decided the GNOME desktop is more to my liking. I would like to remove KDE to free up some disk space. When I first installed it I followed the Guild in the Wiki, and selected the 'kubuntu-desktop' package and it's dependencies. Is there a way to select it's dependencies for removal?

---

### Post by aysiu on 2007-06-01
How did you install it? If you installed it with *aptitude*, just paste this command into the terminal: ```
sudo aptitude remove kubuntu-desktop
``` If not, [this](http://www.psychocats.net/ubuntu/puregnome) may help.

---

### Post by bobshowrocks on 2007-06-01
ok...I used synaptic to install it, so I followed to instructions you linked to and that seems to have done it. But it also removed several other programs that weren't a part of the KDE install, like VLC player and WINE and Clam AV. Not the end of the world, just not as specific as I had hoped.

---

