---
title: "Cant set default application--kind of"
date: 2008-12-19
forum: Desktop Environments
---

### Post by tdyer on 2008-12-19
I have tried setting the default PDF viewer(right-click on the file, properties, open with tab) to be Adobe 8.1.3. I would personally prefer evince, but the boss man "needs" Adobe.

If I double click a pdf it will open in Adobe, if I click on a link in firefox it will open in adobe, however if I use xdg-open or gnome-open it will open with evince.

One of the programs we use opens Adobe through calling xdg-open for linux, gnome-open for solaris.

How can I change what xdg-open of gnome-open uses?

We are using ubuntu 8.04.

Thanks,

Tristan

---

### Post by mali2297 on 2008-12-19
I think that xdg-open looks in the user-specific file **~/.local/share/applications/defaults.list** and/or the system-wide **/usr/share/applications/defaults.list**. Check if you have any of these files and what they contain.

---

