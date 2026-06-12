---
title: "menu editing how?"
date: 2009-04-11
forum: Desktop Environments
---

### Post by ottosykora on 2009-04-11
I wanted to edit the applications menu in XUBUNTU.
However, when open the menu editor, only upper kind of break line etc is editable, and at bottom the help, but in the middle there is 'external menu' inserted which belogns to 'system'.This can not be viewed nor edited this way by the menu editor apparently

Can someone tell me where the actual application menu is hiding and how can I go and edit it?

Lot of apps which are installed can be accessed only by the searc apps and cmd line, I would like to make menu points for them.

---

### Post by him610 on 2009-04-12
Try this...

Click on Applications->Settings->Main Menu

When the Main Menu opens up, you may notice in the upper right corner there is a widget for New Menu and also one for adding a New Item.

You may use the New Menu to add a new menu if the existing menus do not suit your purpose, and you may use the New Item to add a new application to an existing menu or one you have newly created. 

When you have finished, you may close the Main Menu window. Be sure to check out each newly modified menu to see that it lists the applications you just added.

If each of us learns at least one new thing each day, then we are making progress.

Cheers.

---

### Post by morgengenuss on 2009-04-12
@hgh9mrp: ottosykora was really referring to XUBUNTU (xfce), not ubuntu (gnome).

there are two ways to edit the menu in xubuntu. one is to modify the launchers in /usr/share/applications (you'll need to edit them with root access). the other one is to use a custom menu.xml file and to edit the entries.
method 1 applies to all versions of xubuntu, method 2 only works with xubuntu <=8.10.

---

### Post by ottosykora on 2009-04-13
Thanks, 100% right help with the usr/share/... folder, there all that stuf can be edited.
Apparently the menu editor has no access to that and keeps this as a single entry only.

---

### Post by morgengenuss on 2009-04-14
> 
Apparently the menu editor has no access to that and keeps this as a single entry only. 

no, in reality it's a lot simpler: the menu-editor *just doesn't work*. it has always been this way, so look forward to jaunty, (because it'll be gone there.) for xfce 4.8 (if they keep up the release speed, we might see it in 2011) a fully-fledged menu-editor is underway, implementing all those pretty freedesktop-standards. :)

---

