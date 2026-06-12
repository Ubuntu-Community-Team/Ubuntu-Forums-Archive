---
title: "How many sessions can I have?"
date: 2007-10-25
forum: Desktop Environments
---

### Post by jennymanda on 2007-10-25
I have Xubuntu 7.10 with KDE 3 as an alternative session. Works fine.

I wanted to try out KDE4, so I installed it (500Meg!). However, it doesn't appear in the session selection. Where is it? How do I see it to select it? Is there a limit to the number of sessions/desktop environments? 

TIA

---

### Post by Zorael on 2007-10-25
You have to manually add it, as far as I know.

Nicked from kubuntu.org:
> # Install kdebase-workspace and kde4base-dev.
# These KDE 4 packages install to /usr/lib/kde4 so run:

    * export LD_LIBRARY_PATH=/usr/lib/kde4/lib
    * export KDEDIRS=/usr/lib/kde4
    * export PATH=/usr/lib/kde4/bin/:$PATH
    * export KDEHOME=~/.kde4

# Run some programmes. Plasma seems to work and will run over kdesktop happily. Good luck.
# To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.
**# To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.**

---

### Post by jennymanda on 2007-10-25
Thanks!

---

