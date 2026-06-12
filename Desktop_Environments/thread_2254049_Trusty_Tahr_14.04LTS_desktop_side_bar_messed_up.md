---
title: "Trusty Tahr 14.04LTS desktop side bar messed up"
date: 2014-11-24
forum: Desktop Environments
---

### Post by c-cubed on 2014-11-24
After upgrading to Trusty Tahr 14.04LTS about 80% of the time after a reboot, the sidebar/launcher menu on the desktop displays badly.
The icons appear to have random noise in them making them unreadable. When you hover mouse over icon sometimes it displays text box with application name and sometimes it displays unreadable snowy text box.

Would appreciate some help fixing this. Is there a magic key stroke to refresh the desktop that might get rid of it?:p

---

### Post by c-cubed on 2014-11-25
Discovered that changing settings under "System Settings..." then "Appearance" or "Display" causes desktop manager to refresh Launcher Bar and this causes icons to paint correctly. Also discovered that by tweaking these settings I can get pop-up menu for mouse over to display in readable fashion. However, the effects are NOT permanent and I can't get pop-up menu for "right click" on Launcher Bar icon to display in readable fashion and not all icons display mouse over menu correctly.

Trusty Tahr is NOT trusty.

---

### Post by c-cubed on 2014-11-25
Couldn't wait for a reply on forum so I decided to try:
apt-get update
apt-get upgrade
A large number of updates came through and the problem has been resolved.

---

