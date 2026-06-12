---
title: "No Programs In Kubuntu Panel"
date: 2007-06-06
forum: Desktop Environments
---

### Post by terets on 2007-06-06
I am using Kubuntu 7.10 on a HP dv9000t with all the upgrades.  I installed the nvidia-glx drivers and Beryl and everything works fine.  Except, open programs do not show up in the panel.  I can switch programs using Alt+Tab, but it would be nice if the programs showed up in the panel.  This happens even when I turn Beryl off, making me think that it is not Beryl, but the nvidia-glx drivers or something else.  But then again I cannot be sure as Beryl starts up automatically and I can't stop it from doing that (note that I did not say that I don't know how to stop it, beryl-manager is not in the ~/.KDE/Autostart or anywhere else that would make it autostart, I am still investigating that issue).   I have searched the internet and found nothing on this problem, so I was also wondering if anyone else was having this problem.  And if anyone knows of a solution.  Thanks all for your help.

---

### Post by pbw on 2007-06-06
1. Right click your kicker select "add applet", then select taskbar. I assume this is what you mean. When i turn beryl on, it sometimes messes with my panel layout as well. 

Also, this doesn't solve your issue at all, but try middle clicking on the desktop. It allows you to choose application window as well.

2. At kdm (your login page). Find the option to select session and choose kde instead of beryl, what is already selected. kdm defaults to login to your last used environment. Unless you manually choose otherwise.

-- pbw

---

