---
title: "Gigolo - how can I force a rescan of a network?"
date: 2011-12-01
forum: Desktop Environments
---

### Post by Kronalias on 2011-12-01
Gigolo works brilliantly (as long as you sudo apt-get gvfs-backends to get it to work) but I've run into a problem.

The Gigolo network tab shows all my local PCs and their samba shares, and it seems to have cached these somewhere. If I have a pc called fred on my lan and on fred I have a shared directory called share then Gigolo, in the network tab, shows:
WORKGROUP
..FRED
....share

If I change the directory name on fred from share to foobar then I still get the above when I restart Gigolo (or even after a reboot). What I'd like to see is:
WORKGROUP
..FRED
....foobar

So I need to force Gigolo to rescan the network.

Incidentally, I've searched ~ for 'share' to try to see where Gigolo is keeping stuff (grep -lir share .*) but without success.

Can anyone help, please?

---

