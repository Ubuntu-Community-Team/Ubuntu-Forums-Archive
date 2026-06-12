---
title: "Unstable eth0"
date: 2009-01-06
forum: Desktop Environments
---

### Post by flw on 2009-01-06
Hi all,
I have a bizzare situation with my eth0 interface.  It continually cycles between up and down, with about a second or two in each state.  I've swapped the cabling with another piece of equipment and the problem remains the same.  The remainder of the network is fully functional (I'm posting from another computer on the same network).

My only clue is that this behavior apparently starts when I share my hard drive.  I use 'sudo nautilaus' to configure the shares, but I get some two errors during the share process:
1) saying that my shared directories are 'not well formed'
2) saying that 'unknown key format, since the ACL includes Everyone, so the share is assumed read-only'

For a while everything works great, I can write to the directories and samba is fine.  Then the eth0 interface starts cycling, my Windoz PCs are having trouble maintaining the connection, and eventually everything falls apart.

What the heck is going on???
:confused:

---

### Post by flw on 2009-01-07
Ahh, a little more trouble shooting shows that it is related to the Broadcom BCM 4401 100BaseT chipset, and high traffic loads.  This has been reported as a bug elsewhere in the Internet, but I don't see any fixes here on Ubuntu.org.

What now?
:(

---

