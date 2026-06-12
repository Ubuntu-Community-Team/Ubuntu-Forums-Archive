---
title: "Custom xscreensaver"
date: 2011-12-14
forum: Desktop Environments
---

### Post by m3bik on 2011-12-14
Following this guide found at [http://ubuntuforums.org/showthread.php?t=956024](http://ubuntuforums.org/showthread.php?t=956024)

> **cyfur01 said:**
> One possible hack is to create a psuedo-screensaver that will do the logout action. It's not perfect, but the following will automatically log me out of my session.

1. Create a script to do the logout:
```

cd /usr/lib/xscreensaver
sudo touch logout
sudo chmod +x logout
sudo gedit logout

```
Paste:```

#! /bin/bash
# Mimics the normal logout command
gnome-session-save --kill --silent

```

2. Add this to the gnome-screensaver list:
```

cd /usr/share/applications/screensavers
sudo gedit logout.desktop

```

Paste:```

[Desktop Entry]
Encoding=UTF-8
Name=LogOut
Comment=Logs out the user
TryExec=antinspect
Exec=logout
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver

```
As you can see, I copied this from the antinspect screensaver... works as is, though you could clean up the TryExec line probably.

3. Set this as the screensaver like you normally would, and wait for it to take effect.


Note:
Found one flaw with this... every time I go to change it from the usual GUI menu, it just logs me out :P 
You'll have to edit the preferences from the gconf-editor program, or switch the logout script to non-executable (chmod -x /usr/lib/xscreensavers/logout) before going to change the preferences and set it back to executable afterwards.

I can get a custom screen saver to appear in the gnome-screensaver list of available screensavers.. but it does not appear in the xscreensaver-demo menu.. so I can't use my custom screen saver application in xscreensaver.

Is there away to fix this in Ubuntu 10.04.3?

---

### Post by m3bik on 2011-12-14
or can someone tell me how to get the idle time of the user using shell or python?

---

