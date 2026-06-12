---
title: "Is there a way to enable both  edge scrolling plus edge scrolling at the sametime ?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by Wanas on 2011-05-04
In my mouse configuration I only get to enable edge scrolling or the 2 finger scrolling, there is no option to enable both at the same time, other wise in windows 7 it have the ability to enable both at the same time.

---

### Post by Wanas on 2011-05-09
bump

---

### Post by Copper Bezel on 2011-05-09
Yes, Gnome's mouse settings are limited to commonly useful configurations, but the package gpointing-device-settings includes further options, like having both kinds of scrolling enabled. It's also possible to get very granular with your settings using synclient, but it requires using a startup script, and some synclient settings are reset, somewhat unpredictably, by Gnome's set values for them.

---

### Post by Wanas on 2011-05-09
> **Copper Bezel said:**
> Yes, Gnome's mouse settings are limited to commonly useful configurations, but the package gpointing-device-settings includes further options, like having both kinds of scrolling enabled. It's also possible to get very granular with your settings using synclient, but it requires using a startup script, and some synclient settings are reset, somewhat unpredictably, by Gnome's set values for them.

Thanks that was helpful <3 <3

---

### Post by Copper Bezel on 2011-05-09
Cool. = D Just mark the thread as solved at the upper right.

---

### Post by Wanas on 2011-05-09
I enabled it and it worked so great, but after a restart it didnt work, I have to disable it and enable it again. 
Is there a way to be saved forever ?

---

### Post by Copper Bezel on 2011-05-10
I guess we'll need to use synclient, then.

```
#!/bin/bash
sleep 30s;
synclient VertEdgeScroll=1;
synclient HorizEdgeScroll=1;
synclient VertTwoFingerScroll=1;
synclient HorizTwoFingerScroll=1
```

Put this into a text document, make it executable by editing its Properties in Nautilus on the Permissions tab, and add it in your Startup Applications. If it's still not working on startup, try increasing the delay (the "sleep" value.)

---

### Post by Wanas on 2011-05-10
I will try and I will tell you if it works
thanks

---

### Post by Wanas on 2011-05-11
> **Copper Bezel said:**
> I guess we'll need to use synclient, then.

```
#!/bin/bash
sleep 30s;
synclient VertEdgeScroll=1;
synclient HorizEdgeScroll=1;
synclient VertTwoFingerScroll=1;
synclient HorizTwoFingerScroll=1
```

Put this into a text document, make it executable by editing its Properties in Nautilus on the Permissions tab, and add it in your Startup Applications. If it's still not working on startup, try increasing the delay (the "sleep" value.)

After this it works fine now 
thanks again

---

### Post by Wanas on 2011-06-19
I have another problem in this case:
when I plugin my usb mouse the 2 finger scrolling disables it self until I enable is again. is there a way to fix this ?

---

