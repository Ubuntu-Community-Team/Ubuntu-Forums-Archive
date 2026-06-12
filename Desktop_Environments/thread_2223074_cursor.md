---
title: "cursor"
date: 2014-05-09
forum: Desktop Environments
---

### Post by cmcanulty on 2014-05-09
One of my major headaches in ubuntu has been inconsistent cursor size and color. I recently switched to xubuntu and everything was fine for a few days. I use DMZ black size 48. Now it has reverted again to only being correct in firefox desktop and other places it is small and white. This seems like a really dumb bug.I run about 20 desktops for a library and I want it consistent and uniform.

---

### Post by Dennis N on 2014-05-09
Give this a try:

To prevent the DMZ-white cursor from appearing here and there, be sure DMZ-Black is selected as the default by running:

**[FONT=Courier New]sudo update-alternatives --config x-cursor-theme[/FONT]**

On the left side, an asterisk marks the current default. Follow the directions on the bottom. Log out and back in for any changes to be effective.

---

### Post by cmcanulty on 2014-05-09
Oh I've done that for now a restart fixed it but is a continuing issue is all the ubuntu DEs

---

### Post by cmcanulty on 2014-05-17
Now it has mutated in a very weird way. The admin accounts all have small white cursor the limited user accounts all have the DMZ Black 48pt. Both users are set to DMZ black 48. This is one reason I switched to xubuntu as I want all the library computers uniform and with large black cursors as we have so many seniors with poor eyesight.

---

