---
title: "start - up scripts"
date: 2008-08-31
forum: Desktop Environments
---

### Post by beN..87 on 2008-08-31
could one of you clever fellows pleas point me in the right direction as to how to create a script and where to put it that:

upon start up:

connects to default internet through wicd network manager
signs in to pidgin

(leaves both in the tray rather than opening them up on screen)

danke schon, merci beaucoup

---

### Post by pytheas22 on 2008-09-01
For wicd, I think that all you have to do is start it automatically when you log in and it will connect to any preferred network in range (check the box in wicd that says "Automatically connect to this network" in order to tell it to autoconnect).  To start wicd when you log into Gnome, go to System>Preferences>Sessions, click "Add," name the new program whatever you like, and enter this for the command:

```
python /opt/wicd/tray.py
```

As for pidgin, I also think that as long as you've enabled auto-signon, it will connect automatically when it starts.  So you just need to tell Gnome to start pidgin automatically by adding another Sessions program with this command:
```

pidgin
```

Unfortunately I don't know how to start pidgin in the system tray, but there may be an option to do so in preferences.  But let's at least make sure that the command above actually starts pidgin.

Please let me know if either of these instructions doesn't work.

---

