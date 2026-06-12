---
title: "Where is the configuration of user dual screen?"
date: 2014-11-09
forum: Desktop Environments
---

### Post by Sotai on 2014-11-09
I'm in a circumstance where the screen is unusable after logging into a user, due to incorrect display settings, after a 2nd monitor was hooked up and the settings were changed. This persists after resetting and logging back in. Other users are not affected. I would like to know where is the user configuration that affects these settings, or a way to reset these settings without access to the affected user's desktop. Thanks.

edit: It's at ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

---

### Post by carlwsnyder on 2014-11-09
Try the following command from a shell on either a terminal emulator or other method of getting to a command line:```
ls -la .x*
```
Look for something like .xinitrc or a shell script which executes in the startup.  It will definitely be in that users /home/<username> folder.

---

### Post by Sotai on 2014-11-09
No .xinitrc or anything similar. There was .xinputrc .xinput.d. Removing those does nothing.

---

### Post by Sotai on 2014-11-12
It's at ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

---

