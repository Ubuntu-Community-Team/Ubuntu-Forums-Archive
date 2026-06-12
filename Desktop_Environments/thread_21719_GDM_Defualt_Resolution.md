---
title: "GDM Defualt Resolution"
date: 2005-03-23
forum: Desktop Environments
---

### Post by stevenvu on 2005-03-23
I hope i didn't miss a really obvious solution but the defualt resolution for GDM is hideosly high for me. Is there any way to change it?

This is only concerning the GDM, as soon as i login the resolution changes to the user settings.

---

### Post by Julius on 2005-03-23
LOL, I was going to ask the same question. The resolution that GDM takes arbitrarily can be problematic sometimes. For example, if your GDM resolution is 1280x1024 and your user resolution is 1280x960, after logging out you won't be able to see the options (like shutdown, choose session, etc). But I think this problem has been solved and that GDM now goes back to the default resolution after a session finishes. :P

---

### Post by oobuntoo on 2005-03-23
I installed Hoary Preview yesterday and had the same problem. Still can't find a fix. Not sure if this is a bug. My GDM screen looks like a freakin CIRCLE! The GDM resolution is set to 1600X1200 @ 60Hz by default and can't find way to change it.

---

### Post by statico on 2005-03-23
Maybe it chooses the largest resolution found in the mode lines of your xorg.conf ?

---

### Post by brettl on 2005-03-24
GDM does use the modeline from your xorg.conf.  The priority runs from left to right, so if you add "1280x960" as the left-most and remove any items you don't want (who needs half of them anyway, 768x600 or whatever it was, madness.) you should be fine for GDM.

---

### Post by MicroChris on 2005-03-24
Just run:

```
dpkg-reconfigure xserver-xorg
``` 

Has auto detection and should setup xorg for your monitors best refresh rates. I had the same problem the other day, where the res was making my head feel like it was going to split in two.

Good luck,
Chris

---

### Post by oobuntoo on 2005-03-24
Thank you for the hint, guys! I've got GDM to use the correct resolution. My xorg.conf doesn't have ModeLine. I just removed all "1600X1200" from the Section "Screen" and restart x. Woohoo!! :D

---

### Post by Julius on 2005-03-25
I've done it, and now GDM starts at 1280x960, but the menu is shown off the edges :(

---

### Post by wmcbrine on 2005-03-25
I'm happy with the resolution, but how can I get larger text in the login screen?

---

### Post by stevenvu on 2005-03-25
[QUOTE=wmcbrine]I'm happy with the resolution, but how can I get larger text in the login screen?[/QUOTE]
 ...I still think there should be an easier way, especially seeing as that's the first thing a new user sees. Maybe a dialog during installation?

Thanks for the fix by the way.

---

