---
title: "[SOLVED] Gnome top menu doesn't load properly"
date: 2008-06-11
forum: Desktop Environments
---

### Post by Marthr on 2008-06-11
Hi guys,

I have been doing a lot of stuff with my desktop pc running Ubuntu Hardy 8.04 in the last few days and I think I didn't reboot for 3 days in a row.

Just now I did reboot and when I booted into gnome everything seems fine, except for my top gnome menu. I can do everything as I like, but I can't see or click in the menu.

I'm running compiz-fusion and awn. I don't think I did anything special or weird lately.

I'll post a screenshot so you can see what I'm describing. If you need to know anything else, please ask me.

Thanks for your help!

[IMG]http://www.blogging.doesntexist.com/Screenshot.jpg[/IMG]

---

### Post by aysiu on 2008-06-11
If you create and log in with a test user, does the test user experience the same problem?

---

### Post by Marthr on 2008-06-12
Thank you for looking into this, aysiu.

I checked the GUI from a test account. There were totally no Gnome menus to see. I did have the desktop with wallpaper and two mounted drives on the desktop, but erverything else was gone.
I could also right click on the desktop.
Everything seems to work, except for the gnome menus which just don't load.

---

### Post by aysiu on 2008-06-12
In the test account, what happens if you press Alt-F2? Do you get a run dialogue? If so, type ```
gnome-panel
```

---

### Post by Marthr on 2008-06-15
> **aysiu said:**
> In the test account, what happens if you press Alt-F2? Do you get a run dialogue? If so, type ```
gnome-panel
```

Thanks, aysiu! I fixed it. 

Alt-F2 didn't work at all, so I tried to run gnome-panel from the terminal and found out the program "gnome-panel" didn't exist at all. I reinstalled it and now it functions as it should funtion.

I probably uninstalled something without really paying attention to what I was uninstalling.

Thank you for helping me out and showing me where to look!

---

