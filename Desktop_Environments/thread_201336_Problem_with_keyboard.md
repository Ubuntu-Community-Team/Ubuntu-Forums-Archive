---
title: "Problem with keyboard"
date: 2006-06-21
forum: Desktop Environments
---

### Post by steevman on 2006-06-21
Hi
I have a serious problem with my keyboard layout. Several days ago evething was fine, suddenly (I have no idea why) my keyboard started to behave strange. First of all I can't type Polish characters but I could do without them. The worst thing is that when I try to type a dash ß appears. Many other important keys are also gone. I tried to change my keyboard layout but it doesn't help. I think that there might be somthing wrong with my keyboard driver but when I change keyboard model in the keyboard settings menu, it still doesn't change anything. Maybe I should reinstall keyboard driver using a terminal?
I searched goole and other places for a solution but it seems that I'm the ony one who had this problem. Also nobody knew how to help me on Polish ubuntu forum.
The hardware is ACER Aspire 3002NLC notebook but I think it doesn't matter as everything worked fine several days ago.
Do you have any idea what should I do about it?

---

### Post by Griff on 2006-06-21
Have you installed xgl/compiz by any chance?  I know right after I did I had the exact same layout issue.  What worked for me was the follow statup command:
```
xmodmap /usr/share/xmodmap/xmodmap.us-int
```
This just forces a certain keyboard layout when you log in.  It won't do anything scary to system settings.
You will need to change the (us-int) to the layout that you need, however.
Good luck,
Griff

EDIT: WOO! Glad it worked! :D

---

### Post by steevman on 2006-06-21
I can't believe it! Just one command and everything works fine :-D 
Thanks for your help, I'm very grateful!

---

