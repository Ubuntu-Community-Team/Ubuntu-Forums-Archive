---
title: "How to eliminate rogue keybinding?"
date: 2019-05-17
forum: Desktop Environments
---

### Post by dapfy on 2019-05-17
To access my 10 virtual desktops, I do the following:

```
for i in 1 2 3 4 5 6 7 8 9 10; do
	dconf write /org/gnome/desktop/wm/keybindings/switch-to-workspace-$i "['<Super>${i: -1}']"
	dconf write /org/gnome/desktop/wm/keybindings/move-to-workspace-$i "['<Alt><Super>${i: -1}']"
done
```
On inspection, these settings are still successful.

However, since 19.04, the combinations with 7, 8 & 9 no longer have any effect.  <Super>7 instead pops up an annoying help window.  I can't find where that overriding key binding comes from.

---

### Post by TheFu on 2019-05-17
Pick a different GUI?  There are about 50 choices.

---

