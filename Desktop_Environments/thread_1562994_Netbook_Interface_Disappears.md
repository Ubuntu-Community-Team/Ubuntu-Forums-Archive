---
title: "Netbook Interface Disappears"
date: 2010-08-28
forum: Desktop Environments
---

### Post by Vert on 2010-08-28
I had Ubuntu 10.04 64 bit installed on my Netbook, but decided to install the netbook edition for the 32 bits and the interface. My /home partition was NOT erased and is on a different partition. My problem is when I start Netbook Interface (2d or 3d), the netbook interface disappears and the regular Gnome desktop pops up. I've tried deleting .gnome and .gnome2 directories, but no luck. Also, in the Netbook 2d session, I deleted the bottom panel, but it made the bottom panel disappear in the Gnome Proper Session as well. I thought they were different profiles! Am I incorrect? Thank you for anyone that can help kill this problem, at this time, the netbook interface does not exist on this box for all intents and purposes, so I truly appreciate any help.

---

### Post by Vert on 2010-08-28
I deleted the ~/.gconf folder and the Netbook Edition 3D Interface now works correctly, however, 2D still exhibits the same symptoms as before.

---

### Post by CryNGRoad on 2011-02-05
I was having problems with the 2D interface as well. It would disappear after launching an applictation (e.g. firefox) and the menus and window controls would not be placed in the panel. This occurred after I had removed some packages like evolution and had customised the panels in the regular Desktop Edition session. Mulling around in Synaptic, I found a package called **ubuntu-netbook-efl-default-settings** which was not installed. After installing it, everything was back to normal for me.

---

