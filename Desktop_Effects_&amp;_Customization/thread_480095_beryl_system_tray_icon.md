---
title: "beryl system tray icon"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2007-06-21
I have beryl installed and working fine, i am just wondering if there is anyway i can have it so the system tray icon does not show up when i run beryl.  i looked through the settings and did not see it anywhere but i could have missed it.

---

### Post by 5-HT on 2007-06-21
You can delete *beryl-manager* from your startup programs. 

Edit: misread, sorry. You can just remove beryl-manager if you don't want it at all

---

### Post by ep3w on 2007-06-21
Sorry i will try to clarify more, I still want beryl i just don't want the system tray icon to show up when it is running. is it possible?

---

### Post by aquavitae on 2007-06-21
As far as I remember, the system tray icon is just beryl-manager.  Either remove it from the list of startup services, or unistall it.  I won't stop beryl from working, but you may need to explicitly start beryl  in future (which you can do with a startup script)

---

### Post by xkribble on 2007-06-21
Well I have the reverse problem ... which may help you out.  I right clicked the icon and selected "remove from panel" and it no longer shows in the system tray ... I would like to get it back there but don't know how ... I may have removed the system tray completely as I lost my network monitor icon also ... 

well hope this is in the right direction for ya.

.X.


EDIT: 
Ok well I found the fix to my issue 2 seconds after posting ... what I removed was the "notification area" ... not sure if you can remove Beryl from there but you can remove the notification area as a whole.

---

### Post by notwen on 2007-06-21
```
beryl
``` 
alone will launch beryl w/o the icon in your notification area

```
beryl-manager
```
will launch beryl and give you the red gem in your notification area

Good Luck. =]

---

### Post by ep3w on 2007-06-21
Thanks alot! I will add it to the startup when i get a chance. Thanks again!

---

### Post by ep3w on 2007-06-21
Ok so when i go to terminal and just but in "beryl", desktop cube doesnt work and there is no title bars to my windows and its very buggy.  I restart and go to applications then beryl manager and beryl works fine.  It works fine if i put in "beryl-manager" too, but it brings up the system tray icon still.  Maybe I wlll just deal with it and be lucky beryl works at all, unless there is any easy fix.

---

