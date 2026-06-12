---
title: "Nautilus shows a non-existent device"
date: 2020-01-03
forum: Desktop Environments
---

### Post by kakotako on 2020-01-03
I have Ubuntu 14.04 and Gnome 3.10.4. Since several days ago a non-existent drive has been flashing in the left pane of my Nautilus 3.10.1 window under "Devices" every seven seconds or so.

It flashes on and off too quickly to read. I captured a desktop video and took a screenshot of a flash frame showing a phantom removable 4.1 KB volume.

I have reset the Nautilus preferences with:
```
gsettings reset-recursively org.gnome.nautilus
```
And have deleted:
```
~/.config/nautilus
```
But the flashing drive persists. There is no external drive connected to the computer. fdisk -l doesn't show any partitions beyond what I know I have. I'm certain this has to do with some Nautilus user setting because if I launch it as root the flashing is gone. The reset steps I listed above actually did not remove the bookmarks from my Nautilus panel so I wonder if there is something else I need to reset.

---

### Post by vanadium on 2020-01-03
Time for an upgrade. Ubuntu 14.04 is no longer supported.

---

