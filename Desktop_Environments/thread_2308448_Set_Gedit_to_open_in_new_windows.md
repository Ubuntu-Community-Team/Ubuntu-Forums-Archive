---
title: "Set Gedit to open in new windows"
date: 2016-01-03
forum: Desktop Environments
---

### Post by HerzeleidMeister on 2016-01-03
Is there a way to set Gedit to open in a new window instead of a tab when I already have a txt file open. Its very annoying that its opens within the same area for me as for work I need it to open in two windows. Is there a setting or something? TIA!

I'm running Ubuntu 14.04 LTS with the standard Gedit that came installed. :)

---

### Post by PaulW2U on 2016-01-03
> **HerzeleidMeister said:**
> Is there a way to set Gedit to open in a new window instead of a tab
I'm using gedit 3.10.4 here, Ubuntu 15.10. I don't think that there's a setting that allows you to open a file in a new window.

All I can suggest is a work around which you've probably found anyway. That is to open a new file and then to move the new tab into a new window. 'Move to New Window' is in both the 'Documents' menu and 'right-click on the tab' menu.

---

### Post by vasa1 on 2016-01-03
I don't use gedit and so I don't know if this from 2012 applies to your version: [http://askubuntu.com/questions/219046/configure-gedit-to-always-open-in-new-window](http://askubuntu.com/questions/219046/configure-gedit-to-always-open-in-new-window)

And this from 2011: [http://askubuntu.com/questions/75671/why-does-gedit-keep-randomly-opening-new-instances-when-opening-files-from-nauti](http://askubuntu.com/questions/75671/why-does-gedit-keep-randomly-opening-new-instances-when-opening-files-from-nauti)

---

### Post by buzzingrobot on 2016-01-03
Vasa's first link includes a post suggesting an edit of /usr/share/applications/gedit.desktop to make the 'Exec' line read like this: 
> Exec=/usr/bin/gedit -s %U

"man gedit" explains the '-s' allows gedit to run in 'standalone' mode. Here, on 15.10 Unity, it does open a new instance of Gedit for each file that I click on.  However, opening a file with Gedit's file dialogue creates a new tab in the existing instance.

---

### Post by HerzeleidMeister on 2016-01-06
Awesome, thanks the 4th one (the simple solution) worked for what I need. :)

---

