---
title: "Wallpaper Lost on Logout"
date: 2009-08-10
forum: Desktop Environments
---

### Post by bluntwit on 2009-08-10
I recently switch from Ubuntu to Xubuntu, and I can't seem to figure out how to get Xfce to remember my wallpaper choice between sessions. I have gone to Applications > Settings > Session and Startup, and checked off "Automatically save session on logout".

When I set a wallpaper with Applications > Settings > Desktop, it will change the wallpaper to whatever I select, but if I logout and then log back in, it gets reset back to the default Xubuntu wallpaper.

I have tried logging out, switching to a console using CRTL+ALT+F1, clearing the contents of ~/.cache/session, doing a CRTL+ALT+F7, and then logging back in, but that does not seem to help.

How do I get Xubuntu to remember my selection for a wallpaper through logins? This is pretty much a fresh install of Xubuntu, and its never remembered my wallpaper selection.

---

### Post by manu76 on 2013-02-07
I had the same problem, but I solved using dconf.

1) Install dconf.

2) open dconf 
and go to: org > gnome > desktop > background. 
Then change picture-uri to the file you want.

---

### Post by wildmanne39 on 2013-02-07
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

