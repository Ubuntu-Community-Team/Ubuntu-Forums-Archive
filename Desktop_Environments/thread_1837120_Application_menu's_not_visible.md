---
title: "Application menu's not visible"
date: 2011-09-01
forum: Desktop Environments
---

### Post by masterdam79 on 2011-09-01
Dear list,

I summon your wisdom once more te help me with my quest for the safe return of my application menu bars.

Ok, now serious; have installed Ubuntu, after which I installed xubuntu-desktop using ```
aptitude install xubuntu-desktop
```.
Logged out and back in again with the xfce session and was happy until I discovered that all my application menu's disappeared.

To be clear, I'm not talking about the Applications Menu on the panel or the Window Manager; these work fine.

[IMG]http://www.masterdamonline.nl/forumpictures/Workspace%201_038.png[/IMG]

I'm talking about the top row sub menus within the windows for applications like Firefox, Pidgin, Gimp, KDevelop

[IMG]http://www.masterdamonline.nl/forumpictures/Google%20-%20Mozilla%20Firefox_034.png[/IMG]

All Java applications still have the submenus; LibreOffice, jEdit, Spotify (Java?, Dunno, but got submenus there).

In some appications I can get to the submenu's by pression F10, but strangely enough not using ALT.
They don't appear inside the application's window, but near the clock on my panels.

[IMG]http://www.masterdamonline.nl/forumpictures/Workspace%201_047.png[/IMG]

On my other Xubuntu installation there is no problem.

[IMG]http://www.masterdamonline.nl/forumpictures/Google%20-%20Mozilla%20Firefox_034.png[/IMG]

Can it have somthing to do with me installing xfce onto a normal ubuntu installation in stead of installing xubuntu straight away?


Many many thanks in advance!!!

Richard Reijmers

---

### Post by ajgreeny on 2011-09-01
It could be the reason.  Remove **global-menu** packages, or stop them at least in xfce, and you may get back to what you want.

Or you could see if the menus appear in the top panel if you put your cursor onto it, which is what happens in ubuntu gnome 11.04.

---

### Post by masterdam79 on 2011-09-01
Hai ajgreeny,

Thanks for your reply!
There is no such process active at this moment..
```

(sudo) ps aux | grep global-menu
(sudo) ps aux | grep global_menu
(sudo) ps aux | grep globalmenu

```
Also going to the top or corner of the screen doesn't show the active application's submenu.
I know what you mean though, that there is a globalmenu in Unity.

Any other ideas?

---

