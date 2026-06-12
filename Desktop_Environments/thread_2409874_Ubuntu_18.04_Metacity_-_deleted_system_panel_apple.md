---
title: "Ubuntu 18.04 Metacity - deleted system panel applets - want to reinstall"
date: 2019-01-07
forum: Desktop Environments
---

### Post by milesinnz on 2019-01-07
I thought I was deleting just an invalid applet to the left of the system applets - connect - time - drop down for system functions: The whole lot was deleted.

Is there an easy way to add this panel item back, or where are the applets so I can try and add them back individually ?

---

### Post by milesinnz on 2019-01-08
ah, I found a solution: 
sudo apt-get install indicator-applet-complete
sudo apt-get install indicator-appletfossfreedom-appmenu
sudo apt-get install indicator-applet-session
sudo apt-get install indicator-applet

To add to the panel:

Win+Alt+Right click the panel if using Gnome-Classic or Alt+Right click the panel if using Gnome-Classic (No Effects)

CREDIT: = fossfreedom: Nickname - danger mouse, Ubuntu fanatic since v7.
Blog: [http://xpressubuntu.wordpress.com/](http://xpressubuntu.wordpress.com/)

---

