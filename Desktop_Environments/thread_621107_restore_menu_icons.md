---
title: "restore menu icons"
date: 2007-11-23
forum: Desktop Environments
---

### Post by gabrielp on 2007-11-23
My menus had Icons adjacent to each item ,How do I restore it

---

### Post by Happy_Man on 2007-11-23
....I'm afraid I don't understand your question. Could you post a screenshot?

---

### Post by gabrielp on 2007-11-24
Sorry ,cant capture it ,
Here are more details :Pressing Applications gives menu items ,ie SYSTEM TOOLS ,Pressing on it gives an additional menu of items ,each item had an Icon ,
Now this icons are gone ,

---

### Post by Happy_Man on 2007-11-24
Press alt-f2, enter > gconf-editor and navigate to desktop/gnome/interface and check to see if the option "menus_have_icons" is checked.

---

### Post by Virgofenix on 2007-11-25
Hving the same problem. I can't find the "menus_have_icons" in gcof. Can anybody tell the specific tree address?

PS. Problem happened after updating.

---

### Post by Happy_Man on 2007-11-25
Here's a screenshot, in case you guys are having trouble finding it.

---

### Post by gabrielp on 2007-11-25
Hello Hapy_man
Thanks for your cooperation ,I opened gconf editor but dont have the item you speak of
My gconf2 ver is 2.20 and attached is a screen shot

---

### Post by gabrielp on 2007-11-25
Hi Happy_Man
I finally did it ,I found a way to restore the Icons ,
Under SYSTEM-PREFERENCES-Appearance ,Than under Menus and toolbars I checked
 Show Icons in Menus ,and made sure there is an option of Text besides items ,
This solved my problem 
Attached is a screenshot

---

### Post by Happy_Man on 2007-11-25
Ah yes, tha'ts where the option is! I'm on KDE right now, and having forgotten where the option was and not really wanting to log back into GNOME to check, I decided to go the gconf route (where all options are stored). Glad you managed to figure it out!

---

### Post by Virgofenix on 2007-11-25
You're both right, actually.

What was odd was that my option for "Show Icons in Menus" was ticked and the "menus_have_icons" option was *missing* in gconf. I had to re-tick the "Show Icons in Menus" option for the "menus_have_icons" option to show up in gconf.

I still don't know what caused the problem. Still, after that update, I suffered several other problems, such as my gstreamer codecs not working, and my keyboard preferences changed. Was there ever a report about faulty updates?

Anyway, this can be marked as solved. Thanks.

---

