---
title: "file for Ubuntu menu panel icon?"
date: 2006-12-11
forum: Desktop Environments
---

### Post by Rontie on 2006-12-11
Does anyone know the file path for the icon that is used in the top left-hand corner of the screen next to the Applications menu? I am using Edgy btw

I have tried to change 
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

But that is the icon for the "About Ubuntu' under system menu. I believe it was the right file in dapper but it seems that they have changed it for Edgy.  

Anyways if anyone can help me that would be great i have seen several post looking for an answer but nothing.

---

### Post by bluevoodoo1 on 2006-12-11
I think they changed it to "start-here.png" (I think distributor-logo is symlinked to it.)

---

### Post by Rontie on 2006-12-11
do you know the file path to the file, there are a whole lot of start-here.png's i found. I changed the one in the same folder as the last link i had ( /usr/share/icons/hicolor/48x48/apps/distributor-logo.png ) but nothing.

---

### Post by bluevoodoo1 on 2006-12-11
It will depend on what icon set you're using I suppose. I'm using the Human icon set so I'd check... '/usr/share/icons/Human/48x48/places' as well as all the other sizes (32x32, 24x24, etc.).

---

### Post by Rontie on 2006-12-16
okay well none of that worked so i gave up trying after i had changed over what seemed to be  every ubuntu logo on my computer. However today out of the blue (well it was after todays kernel Update) it just decided to work even though i hadn't messed with anything that you would think would make that happen. The only problem though was that the panel was in 128 pixels instead of 24. And agian it would not change back to anything else.

What did solve the problem, even though the problem makes no sense, is to reinstall gnome-panel. When i did this, it excepted all my changes and now looks exactly the way i wanted it to 4 days ago when i gave up... go figure.

---

