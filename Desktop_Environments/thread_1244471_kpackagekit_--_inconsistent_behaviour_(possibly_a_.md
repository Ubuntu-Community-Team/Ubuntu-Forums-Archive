---
title: "kpackagekit -- inconsistent behaviour (possibly a security issue)"
date: 2009-08-19
forum: Desktop Environments
---

### Post by jtappin on 2009-08-19
I have noticed an annoying inconsistency between the behaviour of kpackagekit on different machines.

On my desktop machine the "remember authorization" option is checked by default (or at least it was until I accidentally forgot to uncheck it at an update a few weeks back).

On two different laptops, the default state is unchecked.

All the machines are running Kubuntu Jaunty from a clean install, but in each case my home directory was preserved from a previous Hardy install. The behaviour was not changed on going to KDE 4.3 from the PPAs.

How can I (a) make the desktop forget the remember setting and (b) make it default to "don't remember"? I've not been able to find any such setting in kpackagekit's menus (such as they are). Alternatively is it possible to make the updates available in the system tray fire up adept instead of kpackagekit?

---

### Post by Crunchy the Headcrab on 2009-08-19
I don't know the answer to your question but I find that kpackagekit is rubbish.  I suggest using synaptic or using basic apt-get instead.  They both work better than kde's own package manager.

---

