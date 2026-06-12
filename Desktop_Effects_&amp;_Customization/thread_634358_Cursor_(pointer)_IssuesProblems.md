---
title: "Cursor (pointer) Issues/Problems"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by jobyjoe on 2007-12-07
Hi all, 
   I am having some problems with my cursor/pointer. I'm new to linux, but have been able to figure everything out till now. I installed some X11 mouse themes from GNOME-Look, but I am having some problems. I selected the theme I wanted, but it only works when I am in a firefox. When the mouse is over the desktop, the cursor is the old style (whiteglass). Because of this, I changed my pointer back to whiteglass. However, when I go to resize a window or hover the cursor over the "X" to close a window, the cursor is no longer whiteglass, but the theme I downloaded. No matter what I do, I can't change it to white glass only. Any help? 


Also, how do you delete some of these mouse themes. I've tried going to Appearance preferences: customize: pointer: selecting the theme I don't want: delete, but that does nothing. I hit delete, and nothing happens. How do I get rid of them? Thanks for the help, 


jobyjoe

---

### Post by smartboyathome on 2007-12-07
1) You may have to log out and then log back in (sounds like your cursor is cached). Try selecting the theme you want again and then logging out/in.
2) You can delete the cursor by deleting the folder for it in ~/.icons.

---

### Post by jobyjoe on 2007-12-07
> **smartboyathome said:**
> 
2) You can delete the cursor by deleting the folder for it in ~/.icons.

Thanks for the help. But how do you get to ~/.icons?? The only icons folder I can find has all the icons for my installed apps in it. How do you get to the right one? 


Thanks, 

JobyJoe

---

### Post by smartboyathome on 2007-12-07
~/ means in your home folder (ie /home/yourusername and ~/ are the same thing). The . in front of icons means it is hidden, so you will have to right click > show hidden folders to see it.

---

