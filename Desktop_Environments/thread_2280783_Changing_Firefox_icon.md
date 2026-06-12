---
title: "Changing Firefox icon"
date: 2015-06-02
forum: Desktop Environments
---

### Post by Jyrks on 2015-06-02
Hey,

I wanted to change the Firefox icon, so I navigated to /usr/share/applications and found the file firefox.desktop. However when reading the file i found that it has:
Exec=firefox %u
Icon=firefox

While custom made desktops read: 
Icon=/opt/idea-IU-141.1010.3/bin/idea.png
Exec="/opt/idea-IU-141.1010.3/bin/idea.sh" %f

I could replace the icon easily by adding adding path to Icon. But my question is where does the desktop file look for firefox?
How can i find the folder where the image is located? And what do %f and %u mean at the end of the path?

---

### Post by Dennis N on 2015-06-02
The rules for icon searching are here:
[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html#icon_lookup](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html#icon_lookup)

Meaning of %u and %f explained here:
[http://askubuntu.com/questions/30210/what-does-u-mean-when-calling-a-command](http://askubuntu.com/questions/30210/what-does-u-mean-when-calling-a-command)

---

