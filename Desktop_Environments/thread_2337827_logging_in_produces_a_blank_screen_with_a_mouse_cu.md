---
title: "logging in produces a blank screen with a mouse cursor"
date: 2016-09-21
forum: Desktop Environments
---

### Post by greg2lapa on 2016-09-21
I just installed ubuntu 16.04.1 with Gnome-shell. When I boot, I land at the login screen. I login and then I see just a black screen with a mouse cursor. 

I have Intel (only) graphics (Sandy Bridge CPU). I have tried adjusting screen brightness. I can access terminals (ctrl+alt+f1). But how do I get GUI? Anybody know a fix?

---

### Post by grege2 on 2016-09-25
The blank screen is a sure sign that Gnome Shell is crashing. What I would try is making a new user and logging in to that account and see what happens. If it is OK then it is some legacy config or extension.

from the terminal sudo adduser greg2lapa-b and put in a new password when prompted. Then sudo reboot and select the new user and make sure Gnome is the selected session. Then see what happens.

After that it might just be as simple as deleting the gnome-shell folder from the .local folder in your old account and logging back in.

---

