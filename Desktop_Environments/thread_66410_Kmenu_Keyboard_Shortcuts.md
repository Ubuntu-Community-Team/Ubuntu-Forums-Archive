---
title: "Kmenu Keyboard Shortcuts"
date: 2005-09-17
forum: Desktop Environments
---

### Post by DarkT on 2005-09-17
I've been having some trouble with my KMenu, basically I added a shortcut to the root of the menu and then when I saved the menu (this was from KMenuEditor) it dissapeared and the association to XF86Terminal keyboard key has remained and if I try to assign it to something else it just sais it's already assigned, giving me no option to reassign it. 
 
So I think I tracked down where the .desktops are kept for custom menus (/home/alex/.local/share/applications/) and deleted the .desktop but no fix there, so I also tracked down .config/menus/applications-kmenuedit.menu and removed all references to this shortcut but again this didn't fix it. It seems that although the keyboard shortcut i stored elsewhere and kept even though the shortcut itself is gone.
I'm using KDE 3.2.4 on breezy kubuntu preview release but I've had this problem before in Hoary so I figure a it's persistant KMenu thing. Any ideas on how I can get my shortcut back?

---

