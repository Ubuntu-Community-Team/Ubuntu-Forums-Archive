---
title: "GDM Custom Session"
date: 2005-08-30
forum: Desktop Environments
---

### Post by twelvegates on 2005-08-30
In the Session Menu GDM lists Gnome and some window managers that are installed via the package system.
Now I'd also like to install a window manager not from the package system.
How can I make a session of a window manager appear that is not installed via the package system?

---

### Post by izmaelis on 2005-08-30
It's taken from [this](http://www.ubuntuforums.org/showthread.php?t=54476) thread and adds Enlightenment to the list of possible sessions. Let us start:
```

sudo gedit /usr/share/xsessions/Enlightenment.desktop/

```
Then put this in the new file:
```

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application

```

Save the file as Enlightenment.desktop That shoul be it now you can login to Enlightenment

---

