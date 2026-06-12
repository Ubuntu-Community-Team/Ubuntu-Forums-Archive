---
title: "Nautilus hangs opening folder in Karmic"
date: 2009-10-31
forum: Desktop Environments
---

### Post by macafyc on 2009-10-31
Hi.

This is the situation:

1. Fresh install of Karmic
2. Nautilus is opened
3. While opening a folder with a large number of files or folders, Nautilus becomes non-responsive, consuming 100% CPU and all icons in desktop disappear.
4. This problem doesn't happen when I open Nautilus as root.

Any idea?

Thanks.

---

### Post by macafyc on 2009-11-01
Hi again.

Specifically it's related with the way Nautilus shows the files.
If I choose icon view there is no problem. Choosing list view reproduces the problem.

Nautilus, opened as root, shows by default icon view files.

---

### Post by macafyc on 2009-11-07
It was a Nautilus corrupted configuration
Folder /home/username/.gconf/apps/nautilus/desktop-metadata was empty!

---

