---
title: "new icons when logging in from different desktop environment"
date: 2019-05-08
forum: Desktop Environments
---

### Post by Claus7 on 2019-05-08
Hello,

using desktop session gnome-flashback-compiz I have noticed a weird behavior of some icons under the indicator session of gnome panel, which, when clicked, it gives you the options to change user, restart, shutdown e.t.c..
This happens also using ubuntu 19.04.

If I logout, login to ubuntu session and then return back to flashback, as a logged in user I come across additional icons indicating that situation (a small bullet point in front of the username and a ticked icon at the end). 

I have not figured out why these icons appear after logging in from another session and not directly during a normal boot. Needless to say that these icons disappear next time I boot normally to the flashback session directly. This happens irrespective of the theme and icons used.

Any idea is more than welcome,
Regards!

---

### Post by Claus7 on 2019-06-12
Hello,

some update: the session change which makes these icons to appear is gnome classic. The icons missing are from user show menu. Enabling and disabling that under dconf: /apps/indicator-session/user-show-menu does not change anything.

The /org/gnome/desktop/interface/menus-have-icons does not have any affect either. Trying to change the size of icons did not change anything as well.

The shell seems to have no effect, since the command: setsid gnome-shell --replace # Press Enter again before closing the terminal.
changes session, yet returning back the icons are not there.

edit: The gnome-shell --replace --mode=classic
changes to classic desktop, yet returning back the same result. The killing of indicator-session-service just removes the whole session icon from panel. Returning to session after logout still no result. 

Regards!

---

