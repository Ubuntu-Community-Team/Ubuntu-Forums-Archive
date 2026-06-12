---
title: "X startup script"
date: 2005-03-03
forum: Desktop Environments
---

### Post by SurreaL on 2005-03-03
Hello!

I've written a script that I would like to run automatically whenever I log into an X session, regardless of which window manager I choose. (I say that because I know how to can make fluxbox run command on login..) I've tried to create a .xsession file, as well as a .Xsession file, and made sure both were executable, and starting with the line #!/bin/bash -l, but neither file seems to be run.

Any ideas?

TIA,
SurreaL

---

### Post by jaybee99 on 2005-03-11
I have the same problem - .xsession is never called...I added a line into /etc/gdm/Xsessions to exec $HOME/.xsession but that breaks everything...all I want to do is use xloadimage to set the wallpaper in windowlab....let me know if you work it out!

---

