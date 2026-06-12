---
title: "Nautilus global scripts location?"
date: 2023-11-03
forum: Desktop Environments
---

### Post by bigsqueeze on 2023-11-03
I am able to place scripts within ~/.local/share/nautilus/scripts and these are available in Nautilus right-click context menu under Scripts. E.g.,

~/.local/share/nautilus/scripts/"My first script"
Open Nautilus > select file > right-click > Scripts > My first script

This works fine but is there a location where I can place scripts (as root) and they will be available for all users?  I tried creating a directory /usr/share/nautilus-scripts and placing scripts there, but this had no effect.

Link to example image:
[IMG]https://ibb.co/qxh5FcH[/IMG]   [https://ibb.co/qxh5FcH](https://ibb.co/qxh5FcH)

---

### Post by vanadium on 2023-11-04
No, there is not. You could, however, create a central directory of your scripts, then symlink that into each user's account.

---

