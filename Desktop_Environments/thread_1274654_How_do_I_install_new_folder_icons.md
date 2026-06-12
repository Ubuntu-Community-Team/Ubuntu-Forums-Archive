---
title: "How do I install new folder icons?"
date: 2009-09-24
forum: Desktop Environments
---

### Post by Vignesh S on 2009-09-24
Alright, I'm making my desktop look better, now there's only 2 things left. 

1. How do I install new folder icons? Doesn't seem to be any options about this in the Appearence preferences. A how to for Ubuntu 8.10, 9.04 and possibly even 9.10 would be greatly appreciated.

By the way, this is the link to the icon theme I want to install:
[http://www.gnome-look.org/content/show.php/W7.icon.theme.1.02?content=109359&PHPSESSID=9576fd3e02ec62d4f8d951310eabc9da](http://www.gnome-look.org/content/show.php/W7.icon.theme.1.02?content=109359&PHPSESSID=9576fd3e02ec62d4f8d951310eabc9da)

2. [http://www.gnome-look.org/content/show.php/Windows+7+trayicons?content=109877](http://www.gnome-look.org/content/show.php/Windows+7+trayicons?content=109877)
Came across these cool tray icons, but I have absolutely no idea how to install them. Clearly the poor guy that was also in my situation had no response for his question. Would I also install them the same way that I would install the folder icons?

Does anyone also know some good gnome icon themes? Links would be greatly appreciated.

---

### Post by Tibuda on 2009-09-24
It is in Appearance preferences. There's a "customize" button that lets you change each theme part individually. But you must install it in the "install" button before clicking "customize".

---

### Post by Vignesh S on 2009-09-24
Thanks, danielrmt. But how about the tray icons?

EDIT: I couldn't install the tray icons the same way as I did with the folder icons. Came up with an error saying "apps" does not appear to be a valid theme."

---

### Post by abdusamed on 2009-09-24
> **Vignesh S said:**
> Thanks, danielrmt. But how about the tray icons?

yea..i lost my network manager icon... dont know where it went :-k. I tried reintalling it, but a message pops up saying it already installed. Then when i go to the taskbar>right click>add panel .. I dont see the network manager two pc icon :confused::confused: where is it?!

---

### Post by Vignesh S on 2009-09-25
How did you try to reinstall them, abdusamed?

---

### Post by mcduck on 2009-09-25
> **abdusamed said:**
> yea..i lost my network manager icon... dont know where it went :-k. I tried reintalling it, but a message pops up saying it already installed. Then when i go to the taskbar>right click>add panel .. I dont see the network manager two pc icon :confused::confused: where is it?!

Network Manager is not a panel applet. It just places it's icon inside the Notification Area, so if you can't see Network manager's icon you need to add the Notification Area-applet t your panel.

what comes to "tray icons", the Appearance-dialog only handles icon themes. This means that you can't use it to change icons for individual applets or programs, only complete icon themes which might or might not include new notification icons. Most applets require you to install their icons into that applet's own directory under /etc.

---

### Post by abdusamed on 2009-09-25
> **Vignesh S said:**
> How did you try to reinstall them, abdusamed?

simple..i went to allmyapps[dot]com and searched Network Manager. I found it by accident cuz it's icon is exactly the same which i lost.. from which u can see if ur connected or not

---

### Post by abdusamed on 2009-09-25
> **mcduck said:**
> Network Manager is not a panel applet. It just places it's icon inside the Notification Area, so if you can't see Network manager's icon you need to add the Notification Area-applet t your panel.

what comes to "tray icons", the Appearance-dialog only handles icon themes. This means that you can't use it to change icons for individual applets or programs, only complete icon themes which might or might not include new notification icons. Most applets require you to install their icons into that applet's own directory under /etc.

im sorry..but i really didn't quite get u ...what u typed is pure ubuntu user language :lolflag:... so i have to add an Notification Area-applet to the tray bar so that i could see the icon which shows 'two' computer which highlight if im connected and dim when im not. To had this.. i have to go to apperance and dig a bit from there.. am i right.?? i will try that

---

