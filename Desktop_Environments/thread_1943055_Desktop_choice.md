---
title: "Desktop choice"
date: 2012-03-18
forum: Desktop Environments
---

### Post by as2000 on 2012-03-18
On the login screen, how do I disable the menu to select which desktop to use? The reason I need to do this is because I just want the default Lubuntu desktop and no other choices available to the user of this computer. This computer is for general house use and I have a disabled person that likes to click on things.

---

### Post by 3Miro on 2012-03-18
Which Ubuntu is it? 11.04 and earlier use GDM, while 11.10 and I suppose 12.04 use lightDM. The choice of environment comes from the display manager and the settings are a bit different.

Check here for 11.10:
[http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

I guess you can look at:
```
/usr/share/xsessions
```
If you use a file manager to delete or move all files corresponding to other sessions, you should be able to force Lubuntu only session for all display manager.

PS: make backups to all files that you delete and write down files that you move so that you can restore back your system.

---

