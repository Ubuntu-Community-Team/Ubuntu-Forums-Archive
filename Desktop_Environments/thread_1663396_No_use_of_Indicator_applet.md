---
title: "No use of Indicator applet"
date: 2011-01-09
forum: Desktop Environments
---

### Post by leviathan8 on 2011-01-09
Hi. I am just wondering if it's possible to disable the indicator applet and let the notification area show up the important notifications and programs in tray. The indicator applet has no use to me, and I would like to keep only the notification area applet on panel. Maybe you don't understand what I mean, but here is an example. On the indicator applet I have 2 icons that are completely useless (sound and mail), therefor it has no sense to keep it there, but, as with the update, rhythmbox unfortunately shows up in the indicator applet instead of the notification area. What I want to do, is to let the notification area applet to handle everything. Please ask me if you didn't understood something. Thanks.

---

### Post by Frogs Hair on 2011-01-09
Right click the icon and select remove from panel. To add items to the panel , right click and select add to panel. I don't think you can add the volume applet to notification area applet , but you can drag the sound preferences icon to the panel.

---

### Post by Krytarik on 2011-01-09
To achieve what you want, remove the volume control and the messages envelope from the panel and otherwise retain the functionality of the indicator-applet for programs which use it:
```
sudo apt-get remove indicator-sound indicator-messages
```
Greetings.

---

### Post by stinkeye on 2011-01-10
```
gnome-volume-control-applet
```
Will place a volume control in the notification area and can be 
added to startup applications.

---

### Post by leviathan8 on 2011-01-10
> **Krytarik said:**
> To achieve what you want, remove the volume control and the messages envelope from the panel and otherwise retain the functionality of the indicator-applet for programs which use it:
```
sudo apt-get remove indicator-sound indicator-messages
```Greetings.

Cheers, that is what I wanted. :D

---

### Post by JTempelm on 2011-04-09
thx this helped me also :)

---

