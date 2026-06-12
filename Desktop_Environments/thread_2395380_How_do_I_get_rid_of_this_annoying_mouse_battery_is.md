---
title: "How do I get rid of this annoying mouse battery is low message"
date: 2018-07-01
forum: Desktop Environments
---

### Post by almark on 2018-07-01
Hi I tried lots of dconf-editor settings to get rid of this annoying mouse battery is low 5% message, see attachment. How can I fix this? 

Regards Mark

---

### Post by vanadium on 2018-07-01
Put a new battery in your mouse?

---

### Post by almark on 2018-07-01
Yes that's definitely the easiest way to go solving this problem but... The logitech wireless mouse is working perfect for weeks while showing this message.... I just want this nagging popup to  go away...

---

### Post by vanadium on 2018-07-01
I found this: [https://askubuntu.com/questions/985963/disable-mouse-battery-low-spam-notification](https://askubuntu.com/questions/985963/disable-mouse-battery-low-spam-notification)
Your battery in fact might already be quite low, which won't prohibit you from using your mouse for quite some more time, though. The workaround posted there is to decrease the warning level, but this unfortunatelly applies to all devices and may result in being warned late for your laptop battery. If you are on a desktop, however, that is not an issue.

---

### Post by almark on 2018-07-01
I tried these settings without result :-\ Strange enough the (changed by me) dconf editor settings don't show in the popup message... So what's going one? I'm sort of new with Gnome since Ubuntu returned to Gnome..

---

### Post by vanadium on 2018-07-01
Sure you successfully altered the settings? Does it also not work after a reboot? Perhaps the lower setting is not even enough for that mouse. Perhaps you also need to set use-time-for-policy off before it relies on the percentage settings. The nuclear option is to disable power manager altogether (first option in that dconf screen). Outraging indeed there appears to be no option anymore to selectively disable notifications from power manager (used to be there in Gnome 2).

---

### Post by almark on 2018-07-01
Hey ! The use-time-for-policy did the trick :-) almost.... The popup appears less frequently. Thanks. Regards Mark

---

