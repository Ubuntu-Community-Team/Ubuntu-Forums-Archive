---
title: "Easy way to add application startup arguments using GUI?"
date: 2016-10-12
forum: Desktop Environments
---

### Post by filolaos on 2016-10-12
Using the GNOME GUI, how do I add arguments to the command that starts  an application? For example, I might want to run Firefox in safe mode  using **firefox -safe-mode**.  Please note that I'm looking for a method that will affect the items in my Favourites panel (permanently), not a one-time-only method.

I know I can edit the application's .desktop  file in /usr/share/applications, but this is tedious. In some other  desktop environments I was able to just open the App  Menu's settings window and edit execution commands right in there; or  else hit alt+F3, find the application, and edit its properties. Anything  like that in GNOME Shell?

---

### Post by deadflowr on 2016-10-12
You can try using alacarte.
It installs the old menu editor where you can find the app highlight the app click on the Properties and edit the command.
```
sudo apt install alacarte
```
runs as alacarte or search for Main Menu.

Hope it helps

---

### Post by filolaos on 2016-10-16
Thanks very much, deadflowr. That is exactly what I was looking for.

---

