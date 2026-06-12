---
title: "Broken search in Nautilus 3.6 on Ubuntu 12.10"
date: 2012-10-22
forum: Desktop Environments
---

### Post by AshenShugar on 2012-10-22
I did a clean install of Quantal, and the first thing I did was add the gnome3-team/gnome3 ppa and install gnome-shell and nautilus 3.6. Nothing else, no messing around with the configuration settings or anything. Right out of the box, the search is broken. Terribly, annoyingly broken. It can only search file/folder names within the same directory. It doesn't search recursively or traverse down the file tree, so it won't find a matching file within a folder in the current directory. Is there a package that I'm missing to make this work? Is anyone else having this problem? This seems to be Ubuntu-specific...

---

### Post by mc4man on 2012-10-24
It's not Ubuntu specific - was removed during 3.6 dev.
Has been patched back in the nautilus git (3.7), may show up in 13.04, may not
Otherwise it's pretty easy to patch & build 3.6.1 or just build & use a git nautilus
(at least thru 3.7.1 as no dep changes to gtk or glib yet

---

### Post by wolfv_1 on 2013-01-03
I have the same problem (still). My current solution is to use synapse, which offers a very good search functionality. Maybe it could work for you, too.

---

