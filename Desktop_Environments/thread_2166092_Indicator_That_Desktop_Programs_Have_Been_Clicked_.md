---
title: "Indicator That Desktop Programs Have Been Clicked To Run"
date: 2013-08-07
forum: Desktop Environments
---

### Post by radacheck on 2013-08-07
Is there a way to indicate that desktop programs have been clicked on to run.  This would be like the KDE desktop which shows a bouncing symbol when an icon is clicked. 
As it is now sometimes I click several times not knowing if the first clicks were working.
Thanks, radacheck

---

### Post by Toz on 2013-08-07
Built-in Xfce functionality includes support for startup notifications. Panel Launchers have a "Use Startup Notification" option that if checked, will displaying a small watch icon next to the mouse cursor when the program is launching. For menu items, you need to specify "StartupNotify=true" in its .desktop file (/usr/share/applications) to get the same effect. One caveat though, the application needs to support the startup notification standard for this to work. Also, its small in size and somewhat difficult to notice.

I'm not sure whether other launcher docks like docky or plank have more visible startup notifications.

---

### Post by radacheck on 2013-08-07
Thank you so much for your quick and complete answer. much appreciated.
radachek,
" It is better to light one candle then curse the darkness"

---

