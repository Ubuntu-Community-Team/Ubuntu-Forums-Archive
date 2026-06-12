---
title: "How to set settings to default in Terminal?"
date: 2009-03-18
forum: General Help
---

### Post by abcuser on 2009-03-18
Hi,
I have created new profile in gnome-terminal and it looks like I have massed something out so there is no menu anymore to change back to default settings. I have tried to uninstall gnome-terminal from Application | Add/Remove... then I have installed it one more time and it looks all settings have preserved.

How to set gnome-terminal to default settings, to use default profile?
Regards

---

### Post by abcuser on 2009-03-18
Hi,
solved the problem in Terminal:
gnome-terminal --window-with-profile=Default
and menu is back then Edit | Profile to remove newly created profile and set Default profile to default start up.

Problem solved.
Regards

---

### Post by geirha on 2009-03-18
Hitting Alt+F2 and typing in the command below should reset gnome-terminal to its default settings. (Note that it will kill all currently running gnome-terminals for your user, so make sure you're not running anything important in a gnome-terminal when you run it)
```
gconftool-2 --recursive-unset /apps/gnome-terminal && killall gnome-terminal
```

---

