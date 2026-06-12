---
title: "Trying to setup TightVNCSERVER and KDE,"
date: 2013-06-01
forum: Desktop Environments
---

### Post by nathansuchy on 2013-06-01
I used tasksel to install kubuntu-desktop and then used apt-get to install tightvnc server. I wrote a config file. I only get a blank screen. My config goes as followed,
> #!/bin/sh
/usr/bin/kwin &
/usr/bin/startkde


# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi


I am using TightVNC Server. I attched a photo of what my vnc server does:

---

