---
title: "cant open places menu"
date: 2010-10-11
forum: Desktop Environments
---

### Post by ramire on 2010-10-11
When i try to open a folder from the menu places,VLC starts.
what happened?

also in terminal:
pi@lot:~$ xdg-open ~pi
 VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)


when i try open folders from desktop all opens correctly
Ubuntu 10.10

tnx

---

### Post by ubunterooster on 2010-10-11
That's creepy.. try ```
apt-get purge vlc
```

(We can reinstall vlc later)

---

