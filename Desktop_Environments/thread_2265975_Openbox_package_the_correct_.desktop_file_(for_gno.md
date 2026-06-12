---
title: "Openbox: package the correct .desktop file (for gnome-session, etc)"
date: 2015-02-19
forum: Desktop Environments
---

### Post by quequotion on 2015-02-19
Back in Saucy, I noticed that ubuntu was [packaging openbox with the .desktop file from 3.5.0]("https://bugs.launchpad.net/bugs/1220257") and I thought that the package had somehow been misnamed in launchpad.

Apparently this was the case, the source packages have been correctly updated. The desktop file however, was not and remained the 3.5.0 version until it was [nonsensically]("https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1255783") [removed]("https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1185502").

Ubuntu has been packaging an outdated .desktop file "data/gnome-wm-properties/openbox.desktop" which should be replaced with the correct file "data/openbox.desktop"

There's no need for any patches against the correct file!

This will simplify the setup of openbox/gnome DEs like [Pantheon Lite]("http://ubuntuforums.org/showthread.php?t=2124220&p=12559934#post12559934")

---

