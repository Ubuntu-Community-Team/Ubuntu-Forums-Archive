---
title: "Lock Permissions on Desktop Background"
date: 2012-11-30
forum: Desktop Environments
---

### Post by firefly2442 on 2012-11-30
In XFCE, is there a way to lock the permissions on changing the desktop background image?  Right now I can right click the desktop and go to "desktop settings" without a password.  Is there a way I can change the permissions for this application to require sudo?

Thanks in advance.

---

### Post by 2F4U on 2012-11-30
> Right now I can right click the desktop and go to "desktop settings" without a password.

These are per user settings not system settings, so why should there be a password? A user should be able to set the background image as he/she wants.

---

### Post by LewisTM on 2012-11-30
2F4U is right but I guess you knew that already.
What if you still want to prevent someone (say a kid) from changing your wallpaper while you are away.
Here's a strategy that might work for you.

1) Rename and restrict xfdesktop-settings
```
sudo mv /usr/bin/xfdesktop-settings /usr/bin/xfdesktop-settings-bin
sudo chmod 700 /usr/bin/xfdesktop-settings-bin
```

2) Create a script that will unlock the settings and run them
```
gksudo leafpad /usr/bin/xfdesktop-settings
```
Contents:
```
#!/bin/bash
gksudo chmod 755 /usr/bin/xfdesktop-settings-bin && /usr/bin/xfdesktop-settings-bin && gksudo chmod 700 /usr/bin/xfdesktop-settings-bin
```
3) Make the script executable
```
sudo chmod +x /usr/bin/xfdesktop-settings
```
Now every time you launch the desktop settings, this script will be executed. 
You should save these instruction in case Xfce gets updated and overwrites your script.

Cheers!

---

### Post by firefly2442 on 2012-11-30
> **LewisTM said:**
> 2F4U is right but I guess you knew that already.
What if you still want to prevent someone (say a kid) from changing your wallpaper while you are away.
Cheers!

You read my mind lol.  Thanks, the script works great.

---

