---
title: "notification ubuntu 9.04"
date: 2009-06-22
forum: General Help
---

### Post by inoe on 2009-06-22
hello all, i want to ask. How can i turn off the notification on right top of ubuntu? when someone online, the notification is show, and when rythembox is play the next track, the notification is show. 

Thank u.

---

### Post by kpkeerthi on 2009-06-22
```
sudo apt-get purge notify-osd
``` and **Reboot**


**Warning:** This will complete turn off 'all' notifications.

---

### Post by VCoolio on 2009-06-22
To disable notifications you usually need to set them in the application that initiates them. Pidgin is less obvious: go to Tools > Plugins > libnotify plugin; select it and configure to your taste, or disable completely. 
For Rhythmbox I don't know, dig into the preferences.

---

