---
title: "Desktop mode problem"
date: 2010-08-25
forum: Desktop Environments
---

### Post by kstella on 2010-08-25
I'm running 10.4 UNR on an MSI Wind U100 and have been pretty happy with it. Then I had the bright idea to try switching to the regular Ubuntu interface. It didn't work; there was some kind of error and then it reverted to the netbook interface.

I thought all was well until I realized that whenever I start up my computer, I don't see the favorites or the menu until I click on the Ubuntu icon in the upper-left corner. They used to appear automatically.

Also, the look of the windows changed: now I see the three minimize, maximize, and close buttons in the upper-left and a title bar. I only saw those when I unmaximized a window; now I see them even while the window is maximized and given a tab on the top panel.

I tried changing themes and switching the desktop mode again, but no luck.

I realize that this is not that big a deal, just a minor nuisance. My computer is otherwise fine. But I'd still like to have the original netbook look back.

The official wiki says that the Desktop Switcher has been deprecated ([https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)). If I remove it, will it restore the original interface?

---

### Post by kerry_s on 2010-08-25
the switcher was always messed up. if you want the normal gnome you need to log out & select it in the session menu.

recommend you do that & while your in gnome, open the file manager & press ctrl+h to see the hidden, delete .gconf, netbook-launcher & .local
log out select the netbook session

hopefully everything will be back to stock just like the first day you booted.

---

