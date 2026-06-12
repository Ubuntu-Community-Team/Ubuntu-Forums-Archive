---
title: "Can't fix broken deps without uninstalling Ubuntu-Desktop"
date: 2008-10-03
forum: Desktop Environments
---

### Post by david.rahrer on 2008-10-03
I've finally run into this problem that so many have before, but I find no real definitive answer for.  I installed the new Gimp 2.6 version from GetDeb.net but had issues with it (first time, always have good luck with them).  I upgraded as always by putting all the debs in one folder and running *sudo dpkg -i *.deb*.

I tried to downgrade but it wouldn't let me without removing Ubuntu-Desktop (always learned not to do that).  So instead, I got the debs for the last version I had installed (that worked) and installed over the newer one as I had done previously.  This time there were problems, and I now have three GIMP packages with broken dependencies.  I can't install or remove anything without dealing with them, and of course, anything I try wants to uninstall Ubuntu-Desktop (and for some reason sane and a few other goodies).

Does anyone have a suggestion here?  Can I force a downgrade and have it reinstall Ubuntu-Desktop?  I would like to screw this up as little as possible ;)  

I really appreciate any help.

---

### Post by onero on 2008-10-03
Actually, ubuntu-desktop is just a metapackage, which means it just lists all the default ubuntu programs as dependencies so that you can install the whole shebang at one go. Nothing will happen if it's removed. If that's the only thing it wants to remove, go ahead and remove the gimp packages and reinstall the old version afterwards.

---

### Post by david.rahrer on 2008-10-03
> **onero said:**
> Actually, ubuntu-desktop is just a metapackage, which means it just lists all the default ubuntu programs as dependencies so that you can install the whole shebang at one go. Nothing will happen if it's removed. If that's the only thing it wants to remove, go ahead and remove the gimp packages and reinstall the old version afterwards.

Ok, just to be clear, does doing so still pose any upgrade issues down the line?  And if I try to reinstall it (ubuntu-desktop), would it try to reinstall all the stuff it carries with it or just acknowledge that they are there?  

I probably should do this once on a virtual install and mess that up ;)

Thanks a lot for the quick reply.

---

