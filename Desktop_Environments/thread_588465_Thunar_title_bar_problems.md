---
title: "Thunar title bar problems"
date: 2007-10-23
forum: Desktop Environments
---

### Post by fineghal on 2007-10-23
So I run fluxbox with Thunar, which I love to death. I use the gnome-settings-daemon to apply my selected theme, but it's only partially applied.

Icons and text etc. are all as they should be, but the title bar is only partially correct. 
It should be reminiscient of OS X, but the colors are all missing. 

Example attatched.
Help appreciated! Do I need to muck about with gtkrc files or something? If I log in normally from GDM to the gnome desktop it works perfectly. However if I log into fluxbox even with the settings daemon running it doesn't work. I also tried starting Nautilus to no avail.

---

### Post by cknight on 2007-10-23
Remember that its Fluxbox (and your Fluxbox style) which controls the titlebar, not Thunar.  Fluxbox manages windows including their border and titlebar.  Thunar manages everything inside that boundry (as it were).  Thus, your OS-X Gnome theme can only be applied to everything within the window, but not the titlebar.  However, do not dispair, there are lots of fluxbox themes out there which have the style and color of OSX.  Check out [http://tenr.de/styles/allstyles.php]("http://tenr.de/styles/allstyles.php") for some great styles.

---

