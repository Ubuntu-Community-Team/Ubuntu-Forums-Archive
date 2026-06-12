---
title: "gnome desktop broken"
date: 2009-12-10
forum: Desktop Environments
---

### Post by gerryg001 on 2009-12-10
All was fine for many months. Just updated to 2.6.24-26 kernel and it broke. Rebooted with -25 kernel, still broken. Last apt/log shows a number of libraries also updated, so I imagine one of those broke me, but none seems to key directly to gnome or the problem.

Top/bottom panels work.
Can launch terminal or browser from panel, then app windows work okay.
Min/restore/max okay from gnome panel.

BUT---
Desktop items appear, but cannot be selected. Desktop directory appears okay on disk. Open terminal and move over a desktop icon, and that item then disappears. The desktop items are painted once, then abandoned. Shutdown from gnome also hangs.

From terminal window, all apps work, and shutdown is normal.

Trying apt-get clean/update/upgrade has not effect, nor did
install --reinstall ubuntu-desktop

Tried apt-get install --reinstall gdm
dpkg-configure gdm
   no change (check on reboot also)

Update- Places/ does not work from panel.
Gnome doc says nautilus handles screen icons.
ergo, this appears to be a nautilus problem.
sudo apt-get remove --purge nautilus && sudo apt-get install nautilus
had no effect.
-------------------------
Okay, (only) after a full reboot, the purge/install of nautilus appears to have fixed everything.

---

