---
title: "Is there an Icon Preview Utility?"
date: 2013-04-07
forum: Desktop Environments
---

### Post by ohnonot on 2013-04-07
hello everybody,

from the time i was using xfce i remember:
when i wanted to change an icon on a panel launcher, i would get a chooser that shows all icons available, by their 'short names'.
by 'short name' i mean: for example inside a .desktop file, i can call an icon just 'terminal' and when i change the icon theme, the terminal icon also changes to the new theme (as opposed to putting in the full /path/to/the/icon.png, then it will stay the same).

i like that functionality. my panel looks tidy even after changing the icon theme.

now i'm using a homebrew Desktop of mostly lxde applications and sometimes i dearly miss this feature.
i mean the functionality is there, but the preview utility isn't.

so, would anybody know if there is some kind of icon preview utility, independent of any desktop environment?

---

### Post by ibjsb4 on 2013-04-07
I have not see an icon preview utility, but it would be nice.  I just go to /usr/share/icons or /usr/share/pixmaps and hunt for what I want.

---

### Post by Frogs Hair on 2013-04-07
If you have a menu edit/main menu application you can navigate to different folders with that by selecting properties icon picture . I am not in XFCE at the moment, but below is the Gnome version.

---

### Post by ohnonot on 2013-04-08
> **Frogs Hair said:**
> If you have a menu edit/main menu application  you can navigate to different folders with that by selecting properties  icon picture . I am not in XFCE at the moment, but below is the Gnome  version.exactly!
the dialog/chooser/whateveryoucallit that opens after you click on the icon in your screenshot.
now i have never seen another way of accessing it other than installing xfce-panel.

so that's my question: does it or sth like it exist as a standalone utility?

edit: just logged into xfce desktop and made a screenshot.

[ATTACH=CONFIG]241098[/ATTACH]

i don't need the ability to actually choose icons for launchers, just that bigger window on the right so i can *see* which icon gets chosen if i use the short name. this is very helpful if you need to chose an icon for a .desktop file  and want to make sure it stays consistent with most icon themes.

thanks.

---

### Post by ohnonot on 2013-04-09
actually, i should have been doing my homework instead of posting here!

i looked at the dependencies for xfce4-panel and found "exo-utils". installing that is possible without installing other xfce stuff. i think it pulled in 2 more libraries. anyways, it contains a utility called "exo-desktop-item-edit", which is 99% exactly what i asked.

voilá!

---

