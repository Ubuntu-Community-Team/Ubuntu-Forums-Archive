---
title: "No desktop after log in, for one user only"
date: 2018-09-01
forum: Desktop Environments
---

### Post by mfleming on 2018-09-01
Hi,

I'd really appreciate suggestions for the following problem, which is occurring with a (relatively) new Ubuntu 18.04 installation (not upgrade from previous version).  One user does not get a desktop after graphical log in. The password is accepted, but then only the background is presented, not the desktop. This did not happen when the user was first created, just started recently, and does not happen with other users. I have tried a number of things, including

rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
dconf -reset -f /
unity-tweak-tool --reset-unity

I have also replaced gdm3 with lightdm and tried both Ubuntu default and Wayland. I have also looked everywhere I could think of for an informative error message, but did not find any reported errors.

I have a number of other Ubuntu 18.04 installations and have not seen this problem, and I don't know how to fix it. Any suggestions would be greatly appreciated.

Matthew Fleming

---

### Post by Claus7 on 2018-09-09
Hello,

some suggestions:
1) please do check if ./Xauthority file belongs to you:
ls -la | grep .Xauthority

if not then change the permissions
sudo chown *user_name*:*user_name* .Xauthority

2) try to install a new desktop environment to check if you can see anything bypassing the desktop (examples mate, flashback)

Regards!

---

