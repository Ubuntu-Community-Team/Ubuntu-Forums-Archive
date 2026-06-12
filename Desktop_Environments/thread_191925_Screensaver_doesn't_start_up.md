---
title: "Screensaver doesn't start up"
date: 2006-06-08
forum: Desktop Environments
---

### Post by oliwally on 2006-06-08
I have just installed Kubuntu 6.06 and drivers for my Nvidia card. All works well. However, the Screensaver doesn't start up automatically after specified time.

Gone to: K Menu - System Settings - Desktop - Screensaver. Using one of the nice OpenGL screensavers and set time to 15mins. It displays well in the preview window to the right and when I hit the 'Test' button in works beautifully, but it won't start after the specified time (regardless of the time I put in - tried 1min). What other settings do I need to adjust?

---

### Post by oliwally on 2006-06-08
bump :)

---

### Post by mluu510 on 2006-06-08
yes, i have the seem problem too.

---

### Post by oliwally on 2006-06-09
> I have just installed Kubuntu 6.06 and drivers for my Nvidia card. All works well. However, the Screensaver doesn't start up automatically after specified time.

Gone to: K Menu - System Settings - Desktop - Screensaver. Using one of the nice OpenGL screensavers and set time to 15mins. It displays well in the preview window to the right and when I hit the 'Test' button in works beautifully, but it won't start after the specified time (regardless of the time I put in - tried 1min). What other settings do I need to adjust?


Does anyone have a solution please?

---

### Post by oliwally on 2006-06-09
[QUOTE=oliwally]I have just installed Kubuntu 6.06 and drivers for my Nvidia card. All works well. However, the Screensaver doesn't start up automatically after specified time.

Gone to: K Menu - System Settings - Desktop - Screensaver. Using one of the nice OpenGL screensavers and set time to 15mins. It displays well in the preview window to the right and when I hit the 'Test' button in works beautifully, but it won't start after the specified time (regardless of the time I put in - tried 1min). What other settings do I need to adjust?[/QUOTE]


Still looking for some help please :cry:

---

### Post by D!mon on 2006-06-11
It's a known issue; go to the /etc/x11/xorg.conf and check the section Monitor in that file;
to enable power saving capabilities there should be a string
```
Option "DPMS"
``` somewhere in that section

---

### Post by padre999 on 2006-06-11
[QUOTE=oliwally]I have just installed Kubuntu 6.06 and drivers for my Nvidia card. All works well. However, the Screensaver doesn't start up automatically after specified time.

Gone to: K Menu - System Settings - Desktop - Screensaver. Using one of the nice OpenGL screensavers and set time to 15mins. It displays well in the preview window to the right and when I hit the 'Test' button in works beautifully, but it won't start after the specified time (regardless of the time I put in - tried 1min). What other settings do I need to adjust?[/QUOTE]

Also see this thread: [http://www.ubuntuforums.org/showthread.php?t=188832](http://www.ubuntuforums.org/showthread.php?t=188832)

It is a bug in KDE...

---

### Post by User_Program on 2006-06-11
I don't use DPMS and I don't know if this will work if you do use it.
Looks to me that KDE is assuming that DPMS is enabled (even if you have power saving off in KDE's Display settings)  So if you dont have the DPMS in your xorg.conf this will work again I don't know if it will work if you do have DPMS enabled in your xorg.conf

To fix this add
> DPMS-dependent=false
to your kdesktoprc file in "/home/user/.kde/share/config" under the "[ScreenSaver]" section.

This happens more times then I can count from distro to distro.  KDE should add a option is the display settings for DPMS for there screensaver.  Or know that you turned off DPMS in the power savings menu and write the line to the kdesktoprc for you.

---

### Post by oliwally on 2006-06-17
> To fix this add
Quote:
DPMS-dependent=false
to your kdesktoprc file in "/home/user/.kde/share/config" under the "[ScreenSaver]" section.


Awesome! Without doing anything else, adding that line to the kdesktoprc file solved the problem (ie. I didn't edit /etc/x11/xorg.conf  and no, it doesn't have the  >Option "DPMS"< line in it).

Thanks so much for your help - people on this forum is fantastic!

---

### Post by Glauco on 2006-06-22
Thanks, guys... It worked!!!

---

