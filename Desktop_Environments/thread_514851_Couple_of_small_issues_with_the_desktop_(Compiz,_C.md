---
title: "Couple of small issues with the desktop (Compiz, Conky, Devil's Pie)"
date: 2007-08-01
forum: Desktop Environments
---

### Post by arelfrost on 2007-08-01
Hello,

so I am having a couple of minor issues...

1. When trying to run Conky on startup with Compiz the problem is that Copmiz puts those shadows around the Conky's window. So the workaround is to run a script like ```
sleep 20 && conky
``` instead of just ```
conky
``` in the Startup section of the session. Well, sometimes it works and sometimes it doesn't, the 20 seconds delay doesn't seem to be enough sometimes.

2. I am also running Devil's Pie on startup to get that terminal window integrated into the desktop and it's the same problem here. I have the script ```
sleep 10 && gnome-terminal --window-with-profile=DesktopConsole
```.

The question is whether there is any way to set the order in which to load those apps at startup. I also tried to set the order property in the Current Session dialog but it doesn't seem to work out, either. Some other applications get messed up, besides, I wanted to start with a clean session and have those apps load at startup.

3. The other thing is when restarting the X server I noticed a change in the Keyboard Indicator on my panel. Normally, it says USA or Rus for the selected language, but after restarting X it displays us or ru. Then, when I try to open the Keyboard Configuration it says that the gnome-settings-manager is not running. Click OK on that  window and it opens as usually. It bothers me, though.

So is the problem just that gnome-settings-manager doesn't start with the new X session? How do I make it start again?

Thanks,
Stan

---

