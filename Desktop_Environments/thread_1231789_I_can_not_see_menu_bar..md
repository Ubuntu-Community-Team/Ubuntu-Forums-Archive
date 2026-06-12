---
title: "I can not see menu bar."
date: 2009-08-04
forum: Desktop Environments
---

### Post by Greasy_Larry on 2009-08-04
I recently installed Ubuntu 9.04 netbook on my Dell mini 10. I did not like the desktop environment and switched it to the standard one, now I can not see the menu bar, as if the menu bar is higher up on the screen. How do I lower it, without the ability to access the menu bar. So I need someway to do it with F-keys.

---

### Post by pastalavista on 2009-08-04
Press alt and click/hold anywhere in the window to drag it where you want.. as long as it's not maximized. You can also right-click the window list entry on the bottom panel.

---

### Post by Greasy_Larry on 2009-08-04
> **pastalavista said:**
> Press alt and click/hold anywhere in the window to drag it where you want.. as long as it's not maximized. You can also right-click the window list entry on the bottom panel.

I do not have any windows open, this problem is as soon as I boot up. Furthermore, there is no task bar. So Alt+mouse does nothing and there is no bottom panel to right click on. Right now I basically have a desktop background viewer.

---

### Post by rossbielski on 2009-08-12
I am having the same issue with my new HP Mini-110 with the same os. When I first installed UNR it worked fine and I could see and control the top and bottom panels. I updated the system and now I have no panels, so absolutely no control.

---

### Post by JayKay3000 on 2009-08-12
dunno if this will work but i've been googling

try pressing alt+f2 

then type in killall gnome-panel

this will re-start the panels

Below is the link that I typed that from with added screen shot

[http://ubuntuguide.net/reload-ubuntu-gnome-or-kde-panels-without-restart-computer](http://ubuntuguide.net/reload-ubuntu-gnome-or-kde-panels-without-restart-computer)


Hope this helps

---

### Post by rossbielski on 2009-09-14
It figured it out. You can fix this problem by reseting your desktop manager. See [this]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") page.

First login to tty1 by hitting CTRL+ ALT + F1

Now login and type

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

then

sudo reboot

Now you should have the default setting with the netbook menu. The netbook menu slows my system so I switched back to the classic desktop with the desktop switcher in the preferences menu. Problem solved for now. Hope this helps.

---

