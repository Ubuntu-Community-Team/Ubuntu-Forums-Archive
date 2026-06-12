---
title: "GTK App slow redraw when gnome-panel not running."
date: 2011-10-11
forum: Desktop Environments
---

### Post by cwhittier on 2011-10-11
I am running ubuntu 9.04 with gnome for a kiosk-like application. The app is meant to be full screen, and users should not have access to the OS. For this reason I have turned off gnome-panel so it is not accessible using the command:

sudo -u ubuntu gconftool -s -t string /desktop/gnome/session/required_components/panel true

I use "true" here so it will launch the app successfully (true is a program recognized by the system, that does nothing but return successfully).

This works, and on restart gnome-panel is not launched. However, when gnome-panel is off, my GTK application has 1 second redraw lags when displaying the contents of a combo box, or creating a pop-up window.

Does anybody know why this might be happening, and how I can get around it?

---

