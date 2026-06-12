---
title: "programs not minimizing to notification area"
date: 2008-12-09
forum: General Help
---

### Post by irie on 2008-12-09
For some reason in the past few days whenever I close Deluge, the program doesn't minimize to the system notification area as before.  The program is still running however.  If I click on the link Applications/Internet/Deluge, the program starts another instance in the background but I never get the GUI.  I tried sudo apt-get install --reinstall ubuntu-desktop but problem still exists.
I also lost my tracker applet icon from the notification area.  Will I need to reinstall the system to get everything back?

Thanks for any help

---

### Post by Therion on 2008-12-09
Are you sure you didn't remove the Notification Area applet from your Gnome Panel?

You can right-click on your Gnome panel and go to Properties and drop the applet for the Notification Area, the Applications Chooser (with buttons), or both, onto your Gnome Panel and see if that solves the problem.  Not sure what else to suggest.

---

### Post by christopher.newell on 2008-12-19
I'm having a similar problem, or possibly the same problem.

I can find my notification area on my gnome panel, but anything that should appear there appears in my Window List (taskbar, to use the Windows term) instead.  For applets like network manager and update notification, they appear as items in the window list, and also as a small window on the desktop with just their respective icon.

---

### Post by christopher.newell on 2008-12-19
I thought it might be useful to include a screenshot to show what I'm getting.  irie, is this what you're getting too?  I don't want to take over your thread, so I'll start a new one if this isn't what you're getting.  If I ran Deluge, it would also show up as a small window with an icon.  All items are also in the window list/taskbar.

---

### Post by christopher.newell on 2008-12-20
I recently installed a new nvidia card with TV-out, and I've set up the TV as a separate X screen.  I had a notification area on both screens, and I guess I confused them.  I removed the TV notification area and everything seems fine now.  Sorry irie, I hope you find a solution to your issue.

---

