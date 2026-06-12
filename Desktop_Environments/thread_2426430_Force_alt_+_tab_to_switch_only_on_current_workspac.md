---
title: "Force alt + tab to switch only on current workspace in Ubuntu 16"
date: 2019-09-09
forum: Desktop Environments
---

### Post by bodo101 on 2019-09-09
[COLOR=#212121][FONT=Calibri][COLOR=black]Going crazy not being able to only switch windows in current active workspace when pressing Alt-Tab. When pressing alt+tab, the window switcher goes thru all windows in ALL workspaces, jumping between workspaces like crazy. I just want to switch windows in the current workspace!  Was able to do that before on Ubuntu 14.[/COLOR][/FONT][/COLOR]
[COLOR=#212121][FONT=Calibri][COLOR=black]Googled and found stuff like:[/COLOR][/FONT][/COLOR]
[COLOR=#212121][FONT=Calibri][https://askubuntu.com/questions/464946/force-alt-tab-to-switch-only-on-current-workspace-in-gnome-shell](https://askubuntu.com/questions/464946/force-alt-tab-to-switch-only-on-current-workspace-in-gnome-shell)[/FONT][/COLOR]

[COLOR=#212121][FONT=Calibri][COLOR=black]But my Ubuntu 16 installation doesn't seem to use/have gnome shell? (not sure how to verify this)[/COLOR][/FONT][/COLOR]
[COLOR=#212121][FONT=Calibri][COLOR=black]Appreciate any hint to get out of this madness.[/COLOR][/FONT][/COLOR]

---

### Post by CatKiller on 2019-09-09
By default Ubuntu 16.04 uses Unity as its desktop environment. You can control the desktop effects in Unity with Compiz Config Settings Manager, which is in the repositories.

---

### Post by bodo101 on 2019-09-09
I've used ccsm to change alt+tab behavior for window management, like using Static Application Switcher. But haven't found where I can control to only switch between windows in current workspace when switching windows. Surely this must be the default behavior people expects?

---

### Post by CatKiller on 2019-09-09
It's the keybindings that you want to look at: there are separate entries for "current workspace" and "all workspaces." You just need to set Alt-Tab to be the one for "current workspace" and something else (or nothing) for "all workspaces."

---

### Post by deadflowr on 2019-09-09
The behavior is set in ccsm > ubuntu unity plugin >  switcher.

---

### Post by bodo101 on 2019-09-10
Thanks CatKiller, deadflowr! Simple as that!

I like the Unity switcher and it's previews, but using the Static switcher because I prefer windows ungrouped. Any way to achieve ungrouping with Unity plugin?

---

