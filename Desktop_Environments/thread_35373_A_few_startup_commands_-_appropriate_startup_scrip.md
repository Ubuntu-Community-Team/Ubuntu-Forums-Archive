---
title: "A few startup commands - appropriate startup scripts?"
date: 2005-05-18
forum: Desktop Environments
---

### Post by metellius on 2005-05-18
Hello everyone

Everytime I start kubuntu, I enter a few commands into the console to start things up. Of course, these should instead be in some smart startup script. Here they are:

xrdb < .Xresources         <-- fix xterm colors and backspace-thingy
xmodmap /etc/xmodmap.conf         <-- enable keyboard sound-control keys etc.

Where should I put them?

Harald

---

### Post by philipacamaniac on 2005-05-18
1. Create a new file in Kate. Type in those commands.
2. Save it as "mysettings.sh" and put it in ~/.kde/Autostart
3. Open a Konsole, and then type "chmod 700 ~/.kde/Autostart/mysettings.sh"

---

