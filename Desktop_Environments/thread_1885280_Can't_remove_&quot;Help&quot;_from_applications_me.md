---
title: "Can't remove &quot;Help&quot; from applications menu"
date: 2011-11-22
forum: Desktop Environments
---

### Post by matt3839 on 2011-11-22
This particular problem is a little menial, but it's driving me absolutely insane.

I've been trying to customize my applications menu, and everything has been going well except for one minor detail: no matter what I do, the annoying "Help" item, with the gnome-help icon, will simply not go away. If I do not add the Help item to a category, manually add xfhelp4.desktop to my menu file, etc. all it does is add "Help" between "Graphics" and "Internet" in the submenu section of the menu, even though their is no sort of entry in the menu file anywhere. I cannot add it to a submenu. I attempted to delete the "Help" item from the /usr/share/applications folder as a last resort, but no dice.

I'm able to edit the contents of the "Help" item like what it does upon execution, but otherwise, it's just....stuck there. It's very weird, especially since *every other* option can be edited, added, removed, etc. perfectly (which, since everything else is set up perfectly, makes this issue a hundred times more annoying...)

Does anybody have a solution to this issue?

EDIT: I can't edit the contents of the menu item, either, it just redirects to some nonexistent Xubuntu documentation file on my computer.

---

### Post by matt3839 on 2011-11-23
Ah-HA! Apparently, you need to explicitly exclude the "Help" item near the top of the menu file. Xfce's configuration is a lot more flexible than I thought; now I remember why I switched to Linux in the first place.

---

