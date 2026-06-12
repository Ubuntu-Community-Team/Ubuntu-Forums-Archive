---
title: "xubuntu shortcut change workspace"
date: 2021-12-18
forum: Desktop Environments
---

### Post by dleyva on 2021-12-18
Hello everybody,

is there any shortcut to change workspace?

Thanks in advance

---

### Post by The Cog on 2021-12-18
A three-finger combination:
Ctrl Alt ->
Ctrl Alt <-

---

### Post by Impavidus on 2021-12-19
ctrl+alt+arrow. It works in two dimensions and when you reach the last workspace, it wraps around. To take the current window with you, use ctrl+shift+alt+arrow. You can use ctrl+F1, ctrl+F2 etc. to jump directly to a workspace, but that only works for the first 12 workspaces. I only use the arrows, at most 3 arrows to any of my 15 workspaces. Those shortcuts are listed in the settings for the window manager. You can change it if you like.

---

### Post by yetimon_64 on 2021-12-19
As well as the ctrl+alt+arrows to move one place left or right, there is also the "middle mouse click" on the desktop for a workspace menu. If you have set many workspaces (15 here) this is a pretty quick method to jump directly to a more "distant" workspace if needed.

There is also a wmctrl command that works well for scripts, or in my case used as an easystroke mouse gesture command, for changing workspaces; **wmctrl -s <number>**. Note this <number> starts at 0 for workspace number 1 and then counts up for subsequent workspaces.
For example to jump to workspace **number 4** my easystroke gesture contains the command **wmctrl -s 3**. Used as an easystroke command I find this the quickest workspace selection method of all. If you try this method with either scripting or easystroke you may need to install wmctrl, I don't think it is in a default installation. To do so "**sudo apt install wmctrl**" will install it.

---

