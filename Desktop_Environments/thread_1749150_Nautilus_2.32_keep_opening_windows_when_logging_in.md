---
title: "Nautilus 2.32 keep opening windows when logging in in Gnome"
date: 2011-05-04
forum: Desktop Environments
---

### Post by aldav on 2011-05-04
Hello, I'm using Ubuntu 10.10. Every time I shutdown the PC, I close all the opened programs. When I turn it back on and I log into Gnome, I get a lot of programs started. Nautilus starts to show a lot of windows of a lot of places I opened in previous sessions. Amarok starts. Document Viewer shows a pdf a opened several sessions ago, and the terminal also is started. None of those programs are available under "Startup Programs" tab in "Startup Application Preferences", and the "Automatically remember running applications when logging out" option is unchecked.
It is extremely anoying closing all those windows every single time I log into Gnome. Please, any help would be appreciated.

---

### Post by Krytarik on 2011-05-04
Remove the content of "~/.config/gnome-session/saved-session".

Greetings.

---

