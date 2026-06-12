---
title: "[SOLVED] Problem with Beryl"
date: 2007-07-25
forum: Desktop Environments
---

### Post by rweinreis on 2007-07-25
Still kind of new to this. Just installed Beryl and got everything working. Updated the system two days later now beryl will not load up. When i Right click it and tell it to load Beryl the windows that i have open will flash afew times then go back to default settings. 

I am running ubuntu 6.10

---

### Post by jcarlock on 2007-07-25
The update may have modified your xorg.conf.  I'd recommend running through the guide you used originally and ensure that all the settings have been retained.

JC

---

### Post by FuturePilot on 2007-07-25
What do you get when you run ```
beryl-manager
```from the terminal? Make sure the Window Manager is set to Emerald too.

---

### Post by rweinreis on 2007-07-26
I get the same window that you get when you right click the red gem in the task bar.  Also when i right click the red gem and go to select window manager the only two options are beryl and metacity

---

### Post by rweinreis on 2007-07-26
Went ahead and basically redid the entire installation. Its working fine now. Thanks for the help.

---

### Post by TKR101010 on 2007-08-02
> **FuturePilot said:**
> What do you get when you run ```
beryl-manager
```from the terminal? Make sure the Window Manager is set to Emerald too.

I get ...

 Xlib:  extension "XFree86-DRI" missing on display ":0.0".

and I'm still trying to fix it :)

---

