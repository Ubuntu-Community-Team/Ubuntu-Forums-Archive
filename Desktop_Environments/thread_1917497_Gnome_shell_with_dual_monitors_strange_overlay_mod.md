---
title: "Gnome shell with dual monitors: strange overlay mode behaviour"
date: 2012-01-30
forum: Desktop Environments
---

### Post by AntoineT on 2012-01-30
Hi fellow Gnome shell users,

I'm using Gnome-shell 3.2 in Ubuntu 11.10 with a dual monitor setup. I've disabled the "workspaces_only_in_primary" key in gconf-editor so that both monitors use workspaces.

The strange thing is that when I hit the Activities corner to get into Overlay Mode, my primary monitors shows thumbnails of windows that appear in the primary monitor **in the current workspace**, but the secondary monitors show thumbnails if windows that are in the secondary monitor **in all workspaces**.

For example, assume I have the following windows opened:

Workspace 1: Chromium in the primary monitor, TB in the secondary
Workspace 2: Gedit in the primary monitor, Evince in the secondary monitor.

If I go into overlay mode while in Workspace 1, the primary monitor will show a thumbnail of Chromium (as expected), but the secondary monitor will show a thumbnail of **both** TB and Evince. Likewise, if I go into overlay mode while in workspace 2, the primary monitot will display a preview of Gedit, while the secondary will show previews of both TB and Evince.

Does anyone know how to get Gnome-shell to only display previews of windows in the current workspace in both primary and secondary monitors?

Best,
Antoine

---

### Post by AntoineT on 2012-02-02
Bumpity bump...

---

