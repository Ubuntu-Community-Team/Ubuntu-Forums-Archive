---
title: "Removing menu items?"
date: 2005-07-29
forum: Desktop Environments
---

### Post by Norrad on 2005-07-29
Hi Everyone,

Is it possible to add/remove a menu item from the places menu in gnome? If so, how?

Kind regards,
Norrad

---

### Post by Sam on 2005-07-29
[QUOTE=Norrad]Hi Everyone,

Is it possible to add/remove a menu item from the places menu in gnome? If so, how?

Kind regards,
Norrad[/QUOTE]
Install [Smeg](http://ubuntuguide.org/#menu-editor).

---

### Post by Norrad on 2005-07-29
But that only lets you edit items in the applications Menu. Is it possible to edit the Places Menu?

---

### Post by hunteramor on 2005-07-29
I have the same question.  "Screensaver" appears twice in my system/preferences menu (did some fiddling) and I'd like to get rid of one. Smeg is ineffective - anyone have any insight on the matter?

---

### Post by Sam on 2005-07-29
[QUOTE=Norrad]But that only lets you edit items in the applications Menu. Is it possible to edit the Places Menu?[/QUOTE]
The only things you can do with the places menu:
1) Create a ~/Documents folder, it will appear under the Desktop icon
2) Open a any dialog box (e.g: gedit), then browse for any folder and clic 'Add'. It'll appear in the places menu.

---

### Post by Sam on 2005-07-29
[QUOTE=hunteramor]I have the same question.  "Screensaver" appears twice in my system/preferences menu (did some fiddling) and I'd like to get rid of one. Smeg is ineffective - anyone have any insight on the matter?[/QUOTE]
Go into /usr/share/applications. This is where the launchers in the menus are stored. The one for the screensaver is screensaver-properties.desktop, there should be a copy of it if you see it twice.

---

### Post by hunteramor on 2005-08-07
[QUOTE=Sam]Go into /usr/share/applications. This is where the launchers in the menus are stored. The one for the screensaver is screensaver-properties.desktop, there should be a copy of it if you see it twice.[/QUOTE]

only appears once - any other ideas?  thanks for the help

---

