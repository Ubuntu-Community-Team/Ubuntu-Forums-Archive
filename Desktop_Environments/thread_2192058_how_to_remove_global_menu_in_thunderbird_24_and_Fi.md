---
title: "how to remove global menu in thunderbird 24 and Firefox 25 Ubuntu 12.04"
date: 2013-12-05
forum: Desktop Environments
---

### Post by rvboutin on 2013-12-05
Hi,
I thought I would post this here as it took me a while to find out and did not found any useful answer for Thunderbird on any forum.
Doing ```
[COLOR=#444444][FONT=Arial]sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt[/FONT][/COLOR]
``` for other applications works but the old trick: ```
[COLOR=#444444][FONT=Arial]sudo apt-get remove firefox-globalmenu thunderbird-globalmenu[/FONT][/COLOR]
``` does not work anymore for Thunderbird or Firefox.
To disable global menu for Thunderbird or Firefox since version 24 and 22 respectively, you need to do this:
[LIST]
[*]Firefox: type "about:config" (ignore warning) and search for "unity", you'll find a parameter called "ui.use_unity_menubar", double click on it or right click and chose Toggle to set the value to False = Done! 
[*]Thunderbird: Edit > Preferences > Advanced > Config Editor (button) > ignore warning and search for "unity", you'll find a parameter called "ui.use_unity_menubar", double click on it or right click and chose Toggle to set the value to False = Done! 
[/LIST]
Hope this help someone :)
Cheers,
Rv

---

### Post by Dennis N on 2013-12-05
Yes it does help. I had been wondering about this, as I prefer no global menu. It also restored my movable firefox menu button which had disappeared when the global menu showed up. Thanks for posting this tip.

---

### Post by roiikkata on 2014-06-11
this actually still helps in ubuntu 12.04 with the "drop box menu" bug where none of the drop box menus work until you disable the global menu in thunderbird.

it must be a problem between the newer updates and thunderbird not being updated .. ? i dont know ..

anyways, thank you! it was bugging the mess out a me ..

---

