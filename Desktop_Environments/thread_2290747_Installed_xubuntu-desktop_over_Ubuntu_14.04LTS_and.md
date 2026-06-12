---
title: "Installed xubuntu-desktop over Ubuntu 14.04LTS and failed"
date: 2015-08-14
forum: Desktop Environments
---

### Post by John_Carver on 2015-08-14
I did this install.
It appeared to install correctly and then I did a cold reboot
Nothing had changed except I saw the xubuntu splash screen and next came unity desktop
Logging out saw the xubuntu splash screen again and then the shut down.
So the question is where did the xubuntu-desktop go?

---

### Post by steeldriver on 2015-08-14
It sounds like you're using auto-login: if so, you may need to disable it temporarily in order to select the new desktop session from the login screen

---

### Post by John_Carver on 2015-08-14
The login screen appears to be unity
I enter the password to continue
If this is auto-login, then I don't know where it is located to disable
Thanks

---

### Post by yetimon_64 on 2015-08-14
>  I enter the password to continueEdit:  If you are entering the password you have not got auto login tuned on. 

When you get to the unity log in screen, where you enter the password, click on the cog/gears icon in the password entry box to get a selection (drop down menu) of sessions available. 
Click on the xfce session and then enter the password. The log in screen will remember what you select and will then always log you into xfce session in future restarts until you change it by the same means back to Unity or whatever other sessions you may have installed.

---

### Post by John_Carver on 2015-08-15
You got it
Thanks
Solved

---

