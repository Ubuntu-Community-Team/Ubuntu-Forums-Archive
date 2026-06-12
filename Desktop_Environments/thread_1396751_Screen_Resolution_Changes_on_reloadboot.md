---
title: "Screen Resolution Changes on reload/boot"
date: 2010-02-02
forum: Desktop Environments
---

### Post by Geir B-J on 2010-02-02
[B]I found this on the forum, i got to the deskto>gnome> but im missing the folder "screen" what to do? Any tips?

Geir

Re: Screen Resolution Changes on reload/boot[/B] 			
 			 			 		   		 		 		I had the same problem, and this worked for me:

- in ~/.config/monitors.xml change the appropriate values (width, height and rate);
- also, in GConf (Applications->System->GConf or gconf-editor in terminal) under desktop->gnome->screen->default->0 change the values to your liking;
- restart X to see if it worked:smile:

Actually, I did step No.2 first, and it didn't help, so maybe it's not necessary, but I've added it here, just in case.

---

