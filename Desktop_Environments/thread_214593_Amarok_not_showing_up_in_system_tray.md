---
title: "Amarok not showing up in system tray"
date: 2006-07-12
forum: Desktop Environments
---

### Post by SimoneDice on 2006-07-12
Ok, now the first thing I know you are going to say is to go to the confirguation of amarok and make sure the check box is checked.  However, I have tried turning it on, and then turning it off and then back on, and nothing I do can get the tray icon to appear.

I'm using Ubuntu and Amarok 1.4.  When I first installed 1.4, I kept getting error codes when I started to run it.  For example, DCop server not running and then a Malform url error.  What I finally was able to do is to install an earlier version, 1.3.9, and then upgrade back to 1.4.  The program is running fine now. 

However, with my user log in, the system tray icon does not show up. If I log into a new user account that I didn't try to run the program while when I was having all the original problems, then the system tray icon does load up.  However, even after selecting the check box to disable the system tray icon, and then re-enabling it, it still doesn't show up.  I tried to delete the files in my ~/.kde/apps/amarok folder, but it still doesn't fix it.

I would like to keep my same log in because I have a lot of other settings.  Does anyone know why this could be happening and/or a fix?  I would like to delete all the setting files associated with this log in, but it looks like I'm either missing some in some other folder I can't find, or there is something else going on.  Thank you for any help you can provide.


Do you know where the files for a users settings are located?  There must be a file that has these settings and within that file, which migh tbe corrupted, is causing this problem.  However, I have been unsuccessful locating this file. 

It might also be a problem with the gnome system tray applet.  However, I have not been able to find any settings file for that.  Does anyone know where that is?

---

### Post by k_smolka on 2007-02-18
I am having the same problem, but a number of my apps are not appearing in the notification area. In addition none of my kde apps like kivio or kdevelop start when i run them.

So it looks like it may be a problem with some of the KDE libs or something.

Karl

---

### Post by navneeth on 2007-02-18
You know, sometimes it happens at start-up, to me at least, that the Amarok icon sits in the top-left corner(!!!), where there is no panel or notification area, for some strange reason! What I usually do is to quit and then restart Amarok. This works. 

If you cannot find the icon anywhere, then end the process and start it again (with relevant check boxes checked, of course). I cannot guarantee that you'd see the icon, but these are just my "methods".

---

