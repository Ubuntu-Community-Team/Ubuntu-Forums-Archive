---
title: "Desktop Preferences menu, all gone?"
date: 2005-02-06
forum: Desktop Environments
---

### Post by nesr on 2005-02-06
Hi.. i installed ubuntu on my laptop yesterday and almost everything is working perfect.. 

Today i booted up my machine and wanted to change theme, but the whole menu "Desktop Preferences" is totally gone? .. How can i restore that menu? .. The "item", "Desktop preferenes" is there but there are none of the font, theme, mouse etc. menu points? ...

Any help is appreciated, this really sucks because the tools in the menu works so great.. 

:(

---

### Post by ilari on 2005-02-06
[QUOTE=nesr]Hi.. i installed ubuntu on my laptop yesterday and almost everything is working perfect.. 

Today i booted up my machine and wanted to change theme, but the whole menu "Desktop Preferences" is totally gone? .. How can i restore that menu? .. The "item", "Desktop preferenes" is there but there are none of the font, theme, mouse etc. menu points? ...

Any help is appreciated, this really sucks because the tools in the menu works so great.. 

:([/QUOTE]
 I think the easiest way is to log in using terminal (ctrl-alt-F1), and to delete folders .gnome* and gconf*. The next time when you log into gnome, the menus should be restored to the default stage. However, deleting the named directories, will LOSE ALL DATA & CONFIGURATION you've made to your Gnome-environment.

---

