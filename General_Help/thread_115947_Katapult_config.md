---
title: "Katapult config?"
date: 2006-01-11
forum: General Help
---

### Post by Cliff76 on 2006-01-11
How do I set the configuration in Katapult? When I installed it in Mepis there was a little sys tray icon that I could right clickon which would give me settings. In Kubuntu there is no sys tray icon and I don't see a dcop entry. I want to change the hot-key associated with it to Win+R.

---

### Post by skaboss on 2006-01-11
[have a look there ;) ]("http://ubuntuforums.org/showthread.php?t=110918&highlight=katapult+change")

---

### Post by ChameleonDave on 2008-03-25
> **skaboss said:**
> [have a look there ;) ]("http://ubuntuforums.org/showthread.php?t=110918&highlight=katapult+change")

The post you link to simply says to use Alt + Space to bring up the app and then Ctrl + C to bring up the preferences.

But what if the reason you want to change the preferences is that your **shortcut keys have no effect**?  That seems to be the problem I have.  If only Katapult's configuration files were documented.

---

### Post by ChameleonDave on 2008-03-25
Ok, the default config for katapult is found at this location: ```
/usr/share/kubuntu-default-settings/kde-profile/default/share/config/katapultrc
```

Edit this file with your favourite text editor, and find the following line:
```
SystrayIcon=false
```

Change "false" to "true".  This made Katapult work for me.

---

### Post by ChameleonDave on 2008-03-28
I wanted to find the source of this error, so I deleted the default configuration file and reinstalled Katapult.  Oddly, the file was not recreated.  It appears it is not created by the application itself, but by KDE, or perhaps Ubuntu's version of KDE.

Right now, I find that if I create a new user and then run Katapult as that user (in KDE3), the app works fine, no matter whether it says "true" or "false" in that configuration file.  Weird.

---

