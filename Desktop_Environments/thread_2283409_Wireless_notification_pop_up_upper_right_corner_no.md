---
title: "Wireless notification pop up upper right corner not displaying."
date: 2015-06-21
forum: Desktop Environments
---

### Post by Pablo_Reyes on 2015-06-21
Hi! Everybody

:(I accidentally clicked the don't show/hide notification option on the pop up notification, that always appears on the upper right corner on the desktop, when the pc is booting up.  The one that says "Wireless connection detected, use network menu ....." and the "connected" pop up too. Any ideas how to get it back? I'm using Lubuntu 14.04.  I only know that xfce-notify daemon is the main one for notifications on desktop.  Thank you for your time, in advance.:)

---

### Post by Rex Bouwense on 2015-06-21
Hi, I found this for Xubuntu which I believe uses the same xfce4 daemon
Turn it off:
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled
Reverse it:
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service

---

### Post by Pablo_Reyes on 2015-06-21
Hi! [COLOR=#000000]Rex Bouwense

[/COLOR]Thanks for the quick reply, :) It seems that it show me so far the connected and when I disconnect  pop ups, I have not seen the detected networks pop up yet, but so far so good.  Any idea of doing this with a dialog window or gui option, like in desktop preferences? :-)  Once again, thank you for your time and help.

> **Rex Bouwense said:**
> Hi, I found this for Xubuntu which I believe uses the same xfce4 daemon
Turn it off:
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled
Reverse it:
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service

---

### Post by vasa1 on 2015-06-21
Also see [http://askubuntu.com/questions/398436/accidentally-hid-a-notification-in-xfce4-notifyd](http://askubuntu.com/questions/398436/accidentally-hid-a-notification-in-xfce4-notifyd)

---

### Post by Dennis N on 2015-06-21
> Any idea of doing this with a dialog window or gui option, like in desktop preferences?
Here is the GUI method of controlling these notifications using dconf-editor, which also gets a mention in vasa1's link. Notice that three types of notifications can be independently disabled here - connected, disconnected, and networks available. Please see the attached image as to where. In Lubuntu, you will need to install dconf-editor. In your situation, uncheck any that still need to be reenabled.

---

### Post by Rex Bouwense on 2015-06-22
Thanks Dennis N.  I did not know that.

---

### Post by Pablo_Reyes on 2015-06-22
Hi! Dennis

I tried that way and it run,but I did not do nothing, it did not even ask me for my super user password, to change system settings:confused:.  It should have to ask super user privileges first to change settings.  Thanks for your time in advance.:)

> **Dennis N said:**
> Here is the GUI method of controlling these notifications using dconf-editor, which also gets a mention in vasa1's link. Notice that three types of notifications can be independently disabled here - connected, disconnected, and networks available. Please see the attached image as to where. In Lubuntu, you will need to install dconf-editor. In your situation, uncheck any that still need to be reenabled.

---

