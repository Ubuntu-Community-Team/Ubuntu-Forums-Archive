---
title: "Ubuntu login screen help"
date: 2009-01-27
forum: General Help
---

### Post by Colinho on 2009-01-27
Hi, i installed a login screen from gnome-look and now i can't login. When i try and log in there is a beige background and the loading cursor, but nothing happens. I am running 8.04. Sorry for the lack of detail but i am writing this from my mobile phone. Can someone help me fix this problem?

---

### Post by adult swim on 2009-01-27
maybe as a quick fix try this
when you get to the login screen, hit ctrl+alt+f2
if that brings you to a text login, go ahead and enter your username and password.  then hit ctrl+alt+f7 and see if there is your desktop.  if not, go back to ctrl+alt+f2 and type in ```
startx
``` and look back in ctrl+alt+f7.

---

### Post by Colinho on 2009-01-27
hi, i tried what you said and the desktop was just the beige and the the loading cursor as well. Then i tried it with startx and i get this error message:

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit : No such process (errno 3): Server error.

Sorry if i have misspelt something it is hard for me to write.

Haha as i wrote this my desktop loaded, thank-you!

EDIT: Perhaps you can help me with another (minor) problem.
My screen resolution is 1440x900, and now that I have set this for all users, the login screen appears small, and stretched. It doesn't take up the full screen and is wider than it should be (the circular cursor is oval). The screen not taken up by the login screen is black. Is there a way I can get the login screen to fill the whole screen?

---

