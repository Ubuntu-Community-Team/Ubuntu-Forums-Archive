---
title: "Upgrading KDE To SC4.5 Beta 2"
date: 2010-06-10
forum: Desktop Environments
---

### Post by zenarcher on 2010-06-10
I have added the backport repo for updating to KDE SC4.5 Beta 2 on my 64 bit Lucid system.  After updating and running sudo aptitude safe-upgrade, I'm still left with something like 163 packages being held back.  Checking with Synaptic, the package holding all the updates back is libqt4-assistant, which Synaptic shows would have to be removed before the other packages can be updated.

Has anyone else encountered this?  Is libqt4-assistant a necessary package, or could it safely be removed? 

Regards,
zenarcher

---

### Post by Zorael on 2010-06-11
I think what's happening is that it wants to upgrade Qt4 to 4.7.0b1, but there is no libqt4-assistant of 4.7.0b1 packaged. So the other 4.7.0b1 libraries conflict with libqt4-assistant beneath its own version (or perhaps libqt4-assistant of /any/ version), and so it has to be removed.

Try doing a full-upgrade and see what solutions it offers. Likely it will want to remove libqt4-assistant and potentially other Qt4 packages of which there aren't any 4.7.0b1 packages.

I can't say why libqt4-assisatnt hasn't been packaged. Perhaps it has been superseded by other packages due to packaging scheme changes? Perhaps it didn't build? Or perhaps it's just not a priority.

---

