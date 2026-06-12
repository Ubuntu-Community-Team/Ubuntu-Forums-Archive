---
title: "compiling ontv errors"
date: 2006-07-24
forum: Desktop Environments
---

### Post by zegenie on 2006-07-24
I'm trying to compile the newest version of ontv, which is version 2.2.0 (the version in the repo is 2.0.0), but it keeps complaining about missing several libraries, which I know are there.

"checking for ONTV... configure: error: Package requirements (gtk+-2.0 >= 2.8.0
        pygtk-2.0 >= 2.8.0
        pygobject-2.0 >= 2.8.0
        gnome-python-2.0 >= 2.12.0
        gnome-python-extras-2.0 >= 2.12.0
        libnotify >= 0.3.2
        dbus-1 >= 0.60
        dbus-glib-1 >= 0.60) were not met:

No package 'pygtk-2.0' found
No package 'pygobject-2.0' found
No package 'gnome-python-2.0' found
No package 'gnome-python-extras-2.0' found"

I find it weird. I've checked in synaptic, and they're all installed, except pygobject (which I can't find) and the gnome-python, which I can't find either. However, since ontv 2.0.0 is already in the repositories, and I can run the current version, I'd assume all the necessary dependencies are met...?

---

### Post by JoWilly on 2006-07-24
You need to install the xxxxx-dev packages, these contain the header files.

---

### Post by zegenie on 2006-07-25
Yeah, I know. but I can't find any pygtk-2.0-dev (or similar) package. feel free to point me in the right direction. I've looked, but I can't find the packages mentioned above. (even though I'm certain I have the pygtk dev package installed).

---

### Post by JoWilly on 2006-07-25
> **zegenie said:**
> Yeah, I know. but I can't find any pygtk-2.0-dev (or similar) package. feel free to point me in the right direction. I've looked, but I can't find the packages mentioned above. (even though I'm certain I have the pygtk dev package installed).

It should be python-gtk2-dev (I have it in edgy, I guess it should also be in dapper).

---

### Post by zegenie on 2006-07-25
Sheesh - I was looking through all packages named python-* yesterday and I'm pretty sure I couldn't find it. Found all the necessary packages just now (also needed python-gnome-extras-dev).

Thanks for the help, I must've been blind :)

---

