---
title: "On Trusty, what is CL program to create desktop configuration file?  On Precise, I us"
date: 2014-05-19
forum: Desktop Environments
---

### Post by johnaaronrose on 2014-05-19
On Precise, I used to create a desktop configuration file with my own GUI wrapper which called the gnome-desktop-item-edit command line program (part of the gnome-panel package) which had the Directory (to create the file in) and --create-new as parameters.

This had #!/usr/bin/env xdg-open as the first line. This seems to give problems in Trusty.

However, I noticed that Arronax (in Trusty) creates these files without that first line. Is there a command line program (to replace gnome-desktop-item-edit) which will do as Arronax does?

PS another question, what should I put as the Exec parameter (in the file) if it is, for example, bash /opt/UniversalMediaServer/ums.sh?

---

