---
title: "&quot;Beryl + aiglx + kde&quot; bad error"
date: 2006-10-28
forum: Desktop Environments
---

### Post by Emess on 2006-10-28
I installed Beryl and aiglx for kde as in [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX) and after restarting x found that the panel was missing as well as the window borders. I switched back to kwin and all was fine. Iv played around with the xconfig and cant figure out whats going on. Any help is appreciated.

[EDIT] tried switching to beryl within kwin and only window borders disappeared this time. perhaps it is something to do with beryl themes, im not quite sure. When i switched back to kwin, the system tray began to flash as icons disappeared and reappeared repeatedly for 10 seconds or so and i received the error 
"The Composite Manager crashed twice within a minute and is therefore disabled for this session."
After switching back and forth again the only issue is that error, the icons no longer flash but the window borders are still missing in beryl.

---

### Post by user1397 on 2006-11-09
> **Emess said:**
> I installed Beryl and aiglx for kde as in [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX) and after restarting x found that the panel was missing as well as the window borders. I switched back to kwin and all was fine. Iv played around with the xconfig and cant figure out whats going on. Any help is appreciated.

[EDIT] tried switching to beryl within kwin and only window borders disappeared this time. perhaps it is something to do with beryl themes, im not quite sure. When i switched back to kwin, the system tray began to flash as icons disappeared and reappeared repeatedly for 10 seconds or so and i received the error 
"The Composite Manager crashed twice within a minute and is therefore disabled for this session."
After switching back and forth again the only issue is that error, the icons no longer flash but the window borders are still missing in beryl.i had this same problem man, but in kubuntu edgy, all the same though, since aiglx is installed by default in edgy.

could never figure this one out.  now im back to dapper.

---

### Post by Faelar on 2006-11-30
Your problem seems to be a graphics driver issue.
Check out the latest driver for your video adapter, and set properly your XOrg configuration file in /etc/X11/xorg.conf
I had the same problem with an Nvidia Card... I solved that installing the latest driver from Nvidia website... I got the 9629 version of the official drivers, configured xorg.conf and now all is going smooth!

I'm available for further questions!

Enjoy Ubuntu!

bYe,
*Andy*

---

### Post by coolclassic on 2006-11-30
Same problem but solved with driver mentioned above.

---

