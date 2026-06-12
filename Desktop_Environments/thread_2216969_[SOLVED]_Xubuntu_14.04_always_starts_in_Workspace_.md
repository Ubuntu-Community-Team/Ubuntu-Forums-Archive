---
title: "[SOLVED] Xubuntu 14.04 always starts in Workspace #2."
date: 2014-04-14
forum: Desktop Environments
---

### Post by lethalfang on 2014-04-14
I had a clean install of Xubuntu 14.04 (RC, I guess), but with home directory from a previous installation. 
Minor annoying thing. When I boot, it boots into Workspace #2, not #1. Odd. This only happens on this desktop with a previously installed home directory. 
Anyway knows what's up with that?

---------------------
Basically, I went to Settings->Session and Startup->General->Automatically, to check the "save and restore sessions on logout" box. Reboot. Uncheck. Reboot again. Somehow that must've cleared up some old config files and things are normal now.

---

### Post by buzzingrobot on 2014-04-15
XFCE has an option to save and restore sessions on logout. (Settings->Session and Startup->General->Automatically save session on logout).  Perhaps that was enabled in the previous install and an old config file is in use?

---

### Post by slickymaster on 2014-04-15
You can confirm what values are being loaded by xfce4 in your last login into your system, including the workspace.

If you navigate to your **$HOME/.cache/sessions** folder, you'll find a lot of files there, including some empty xfwm4- files and among them you'll have a particular file named **xfce4-session-HOST_NAME:0**, where HOST_NAME is of course the name of your local machine.

If you run the cat command in this file, you'll be able to check the workspace that's been loaded for your actual session. See below the example for mine:```
~$ cat /home/slickymaster/.cache/sessions/xfce4-session-PaPir:0
[Session: Default]
<... snip ...>
<... snip ...>
<... snip ...>
Count=5
LegacyCount=0
**[COLOR=#ff0000]Screen0_ActiveWorkspace=1[/COLOR]**
LastAccess=1394502824
```

---

### Post by lethalfang on 2014-04-18
Mine shows Screen0_ActiveWorkspace=1, even though it keeps booting into Space #2. Hmmm.......

---

### Post by lethalfang on 2014-04-18
> **buzzingrobot said:**
> XFCE has an option to save and restore sessions on logout. (Settings->Session and Startup->General->Automatically save session on logout).  Perhaps that was enabled in the previous install and an old config file is in use?

It was unchecked.

Anyway, I checked it. Rebooted. Then unchecked it again. Rebooted again. And now it seems to be normal, booting into Space #1. Hmm. :D

---

