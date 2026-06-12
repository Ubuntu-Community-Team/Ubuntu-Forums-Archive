---
title: "deleted items folder on desktop"
date: 2010-03-15
forum: Desktop Environments
---

### Post by pernest on 2010-03-15
Hi

I'm trying to migrate my parents away from windows XP and I want to configure the gnome desktop to make the transition as pain free as possible.

1) Is it possible to to have a link to the deleted items folder on the desktop?

2) Is it possible to place a logout/switch off menu item into the main menu?

---

### Post by mcduck on 2010-03-15
1. Press Alt-F2 and run "gconf-editor". Use that to browse to apps/nautilus/desktop and enable the "trash_icon_visible" -option. 

2. This is possible, but you'll loose some functionality provided by the panel applet since it's not possible to have the menu options and the default panel applet at the same time. But if you still want to do it, right-click on the "Indicator Applet Session"-applet in your panel (the one in top right corner of your screen that now has the shutdown options) and select "remove from Panel". Once you remove this applet from the panel the shutdown options will appear in System menu.

---

### Post by coffeecat on 2010-03-15
> **pernest said:**
> 2) Is it possible to place a logout/switch off menu item into the main menu?

> **mcduck said:**
> 2. This is possible, but you'll loose some functionality provided by the panel applet since it's not possible to have the menu options and the default panel applet at the same time. But if you still want to do it, right-click on the "Indicator Applet Session"-applet in your panel (the one in top right corner of your screen that now has the shutdown options) and select "remove from Panel". Once you remove this applet from the panel the shutdown options will appear in System menu.

@pernest, if you want (nearly) the best of both worlds, you can do what mcduck says so that the shutdown option appears in the System menu. Then right-click anywhere on the upper panel > Add to panel and choose the 'Shut Down' applet. This offers fewer options than the Indicator Applet Session applet, but you get the choice of using the menu or clicking on a panel applet to shutdown/reboot. If you want to move the Shutdown applet, right-click on it, choose move, move it laterally with the mouse and then left-click when you're done.

---

### Post by pernest on 2010-03-15
Thank you both, brilliant stuff.

How do I mark this question as solved?

---

