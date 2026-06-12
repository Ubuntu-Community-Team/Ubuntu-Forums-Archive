---
title: "Changing keyboard shortcuts for changing layouts"
date: 2022-05-06
forum: Desktop Environments
---

### Post by rubikserega on 2022-05-06
Hello.
Please tell me how to change the keyboard shortcut to change the layout to ctrl + shift in Ubuntu 22.04
1. gnome-tweaks - not working
2. This patch
sudo add-apt-repository ppa:nrbrtx/xorg-hotkeys
sudo apt-get update
Doesn't work either.

---

### Post by DuckHook on 2022-05-06
Welcome to the forums, rubikserega,

Jammy (22.04) defaults to Wayland for display server; it is no longer X.Org. So X.Org utilities no longer work. I recommend that you uninstall the utility that you installed, then purge the PPA.

It bears noting that installing PPAs is fraught with huge security risks and is not recommended. If you are new to Linux or Ubuntu, the link in my sig is worth reading: Linux is Not Windows

If you are running vanilla Ubuntu with Gnome, the default key combo for changing layouts is: <Super> + <Space>. This can be changed in Keyboard Shortcut Settings to the key combo of your choice, but I do not recommend changing defaults because you could clobber shortcut combos that belong to other apps. It's always best to leave your bare metal install at its defaults until you become a power user and know exactly what you are doing.

---

### Post by DuckHook on 2022-05-06
*Thread moved to **Desktop Environments** as the more appropriate forum.*

---

