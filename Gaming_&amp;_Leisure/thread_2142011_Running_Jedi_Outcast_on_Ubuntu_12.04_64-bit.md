---
title: "Running Jedi Outcast on Ubuntu 12.04 64-bit"
date: 2013-05-04
forum: Gaming &amp; Leisure
---

### Post by Isamu715 on 2013-05-04
I want to run the GNU/Linux port of Jedi Outcast on Ubuntu 12.04 64-bit. I have copied the *base* folder from my game CD and applied 1.04 patch. The instructions are for Ubuntu 12.10 but I thought it might work for 12.04 too.
From the instructions:
```
Needed libraries on Ubuntu 12.10 64bit:
sudo apt-get install ia32-libs libxxf86dga1:i386
```
*ia32-libs* installs fine without any problems but when I try to install *libxxf86dga1:i386* I get this:
```
The following packages will be REMOVED:
  brasero gnome-media gnome-session gvfs gvfs-backends gvfs-daemons gvfs-fuse
  libxxf86dga1 mplayer nautilus nautilus-sendto nautilus-share ubuntu-desktop
  x11-utils xorg
```
Obviously, I cannot continue as this looks like it will completely break the system. Has anyone succeeded in running this game on Ubuntu 12.04 64-bit? How can I do this?

UPDATE:
With the latest version Jedi Outcast *libxxf86dga1:i386* is no longer required, thus the problem no longer persists and the game runs as it should.

---

