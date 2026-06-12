---
title: "How do I disable the notification that appears when I change the screen brightness?"
date: 2015-09-12
forum: Desktop Environments
---

### Post by David_Bjrhn on 2015-09-12
I find this specific notification annoying and distracting - is there a way to disable it? I'm a novice user and I'm running Xubuntu 15.04.

---

### Post by Dennis N on 2015-09-13
You can disable them all, but probably not just one type of notification. A method is described here:
[http://danson.grafidog.com/2012/08/how-to-disable-popup-notifications-in.html](http://danson.grafidog.com/2012/08/how-to-disable-popup-notifications-in.html)

---

### Post by vasa1 on 2015-09-13
When I run```
gsettings list-recursively | grep notifi
```I see this:```
05:05 PM ~ $ gsettings list-recursively | grep notifi
org.gnome.nm-applet disable-disconnected-notifications false
org.gnome.nm-applet disable-vpn-notifications false
org.gnome.nm-applet disable-connected-notifications false
apps.gnome-mplayer.preferences show-notification false
org.gnome.desktop.screensaver show-notifications false
org.gnome.desktop.notifications application-children @as []
org.gnome.desktop.notifications show-in-lock-screen true
org.gnome.desktop.notifications show-banners true
com.ubuntu.update-notifier regular-auto-launch-interval 7
com.ubuntu.update-notifier end-system-uids 500
com.ubuntu.update-notifier release-check-time uint32 0
com.ubuntu.update-notifier show-apport-crashes true
com.ubuntu.update-notifier no-show-notifications false
05:07 PM ~ $ 
```
[http://askubuntu.com/questions/88051/how-can-i-stop-gnome-shells-drive-pop-up-notifications](http://askubuntu.com/questions/88051/how-can-i-stop-gnome-shells-drive-pop-up-notifications)
and
[http://askubuntu.com/questions/574303/how-do-i-re-enable-disabled-network-notifications-never-show-again-in-unity?rq=1](http://askubuntu.com/questions/574303/how-do-i-re-enable-disabled-network-notifications-never-show-again-in-unity?rq=1) may offer pointers on how to proceed.

My system (Openbox session in Lubuntu 14.04) doesn't show any OSD notification when I increase or decrease screen brightness.

---

### Post by David_Bjrhn on 2015-09-13
Thanks for the replies.  I still don't know how to disable OSD for screen brightness, but at least I can now configure a few Notify-OSD settings by following [this guide]("https://askubuntu.com/questions/128474/how-to-customize-on-screen-notifications"). :)

---

