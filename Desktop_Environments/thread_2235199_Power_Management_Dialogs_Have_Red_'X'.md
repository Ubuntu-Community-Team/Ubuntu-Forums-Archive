---
title: "Power Management Dialogs Have Red 'X'"
date: 2014-07-19
forum: Desktop Environments
---

### Post by sgharp on 2014-07-19
I'm running Ubuntu Server 14.04 with kubuntu-desktop.

When I try to run the Power Management applet from System Settings, I get a red X and a message 'Power Management configuration module could not be loaded.  The Power Management Service appears not to be running.  This can be solved by starting or scheduling it inside "Startup and Shutdown / Service Manager".'  

In the Startup and Shutdown applet, Power Management shows that it's running.  When I try to manually stop and restart the Power Management System, I get a message, 'KDE Power Management System could not be initialized.  The backend reported the following error: No valid Power Management backend plugins are availalbe.  A new installation might...'.  However, it still shows that it's running.

Which plugins to I need?  apt-get install what?

My eventual goal is to disable the inactivity screen lock.  It's driving me crazy(er).

Is there a configuration file/setting somewhere that I'm missing?

Thanks for any help/

---

