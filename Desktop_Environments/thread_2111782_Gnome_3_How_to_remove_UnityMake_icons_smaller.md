---
title: "Gnome 3: How to remove Unity/Make icons smaller?"
date: 2013-02-02
forum: Desktop Environments
---

### Post by Baldrick_NZ on 2013-02-02
I've just installed Gnome 3.6 on a 16Gb USB stick to play with and it works fine. 

However, to help save space, how can I remove all versions of Unity (2D & 3D) safely? When I try via Synaptic, it tells me 'Ubuntu-Desktop' has to be removed. If so, that would leave me with no desktop at all?

Also, the desktop icons, both in the native launcher and Applications when using 'Activities' seem huge. Is there anyway to reduce the size of these icons?

Any help would be much appreciated.

Baldrick.

---

### Post by stinkeye on 2013-02-02
Ubuntu-Desktop is a meta package that depends on all of the packages in the Ubuntu desktop system.
Any time you remove a package needed for the Ubuntu desktop system, the Ubuntu-Desktop
package will be removed also.
eg
If I remove the Ubuntu-Desktop package it does not remove any other package.
Be very careful, though to note what else is going to be removed
when uninstalling unity packages.

Reinstalling Ubuntu-Desktop will pull in all the packages necessary for an Ubuntu/Unity session.

---

