---
title: "list users with login manager"
date: 2005-12-25
forum: General Help
---

### Post by rjs on 2005-12-25
I am completely confused. I had my laptop on auto-login for a long time, but now my gf has to use it too, so i changed it to have a login screen again. The only problem was that no matter what i do in the 'user' tab of 'login manager' it still comes up with a box asking for user name and password rather than a list of users. I have the show list and inverse selection buttons ticked and no users ticked (which is the defualt) and from what i could tell from the help should mean that a list appears. I have also tried almost every other possible combination. The strangest part is that changing settings in other tabs seems to have an effect whereas it doesnt in the user tab. wtf?

Anyone got any ideas?

btw, i'm running kde3.5 if that makes any difference.

paz y amor,
-rjs.

---

### Post by infoseeker on 2005-12-26
I tried to change that too.  KDE 3.5 here as well.  The only way I could get the login list was to change from KDM to GDM.  It is possibly done this way for security reasons, maybe ?

> sudo dpkg-reconfigure gdm


I am a single user so KDM with autologin is what I am using ;)
The second user I created is more for experimental use than anything else.

---

### Post by anil_robo on 2005-12-26
I use GNOME, but I have a comment.

As per my experience, some login themes would not allow displaying a "user list". If you have installed a personalized theme from somewhere, try selecting the default login theme in KDE.

---

