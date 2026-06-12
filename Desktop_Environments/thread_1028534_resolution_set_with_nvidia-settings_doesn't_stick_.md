---
title: "resolution set with nvidia-settings doesn't stick after logoff"
date: 2009-01-02
forum: Desktop Environments
---

### Post by c-shadow on 2009-01-02
Nvidia 7600GS card, using driver 180.08 in intrepid (same problem with 177). I swapped my old CRT monitor for new philips 22" LCD, connected to DVI output. I have also LCD TV connected to VGA (separate X screen configured in xorg). Everything works fine after setting the proper native resolution 1680x1050 for the primary LCD monitor. But on next logon resolution drops to 1360x768 :(
Strange, maybe it is a coincidence but  this is exactly the res of the secondary screen (TV)...
This happens only with one user on the machine, if some other user logs on, the screen resolution is fine, 1680x1050.
It seems to me that nvidia-settings stores some info per user, but where?
All I was able to find was the ~/.nvidia-settings-rc, tried deleting that but no luck...
Xorg.conf and xorg log are attached

---

### Post by MighMoS on 2009-01-03
If you're using nVidia's control panel to configure your settings, you need to tell it to load those settings on startup (this is nonobvious).

Go to System --> Preferences --> Sessions

Add a new Item, and the command is ```
nvidia-settings -l
```. You can name it something like "Load NVidia Settings".

---

### Post by c-shadow on 2009-01-03
That doesn't help. Even tried running it manually after logging in.
An man page for nvidia-settings says:
```

Values such as brightness and gamma, XVideo attributes, temperature, and OpenGL settings can be queried and configured via nvidia-settings.

```
So i don't think it is going to change the screen resolution.
Before i changed the monitor, everything worked fine for all users.

---

### Post by pwaldo on 2009-01-03
> **MighMoS said:**
> If you're using nVidia's control panel to configure your settings, you need to tell it to load those settings on startup (this is nonobvious).

Go to System --> Preferences --> Sessions

Add a new Item, and the command is ```
nvidia-settings -l
```. You can name it something like "Load NVidia Settings".I have a similar problem; I want to set xgamma.  I tried your suggestion, but it does not seem to run, as the gamma is just the default after gnome startup is finished.  Is there a startup file like .xinitrc that can be used?

---

### Post by c-shadow on 2009-01-04
Found it!
It's the file ~/.config/monitors.xml and it can be changed via the gnome-display-properties. Which is BTW completely useless if you are using nvidia proprietary driver. My home folder is quite old and it seems to be some remnant from the past :-)

---

