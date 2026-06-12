---
title: "Gnome-panel crashes after upgrade to Feisty"
date: 2007-04-21
forum: Desktop Environments
---

### Post by sverre76 on 2007-04-21
Hi all!

I upgraded to Feisty Fawn yesterday och the installation complained about something during install of some font-packages (I think), and then tried to reverse the installation. That didn't seem to work though because everything looks like i have Feisty installed now, with new versions of applications like firefox, openoffice etc. 

I saw in another thread that I could run these commands to verify that Feisty had been completely installed:

```
 sudo apt-get update && sudo apt-get dist-upgrade
 sudo apt-get -f install
 sudo dpkg --configure -a
```

From what I can understand everything is ok with that install, nothing new was installed and there was no complaints.

But now, I have some issues, and the largest one is that gnome-panel crasches every time I startup the computer (and gnome). Gnome-panel tries to restart itself about 10 times or so before giving up. During that time a lot of error messages flashes on the screen about not being able to load applets (trashbin-applet for example) or that it is closing down because it has discovered another instance of panel already running.

I tried in sypantic to make a complete removal of gnome-panel, and then deleted the .gnome .gnome2 .gconf .gconfd and .metacity directories from my home directory and then rebooted the computer. Then all previous gnome settings are back to default, but if I re-install gnome-panel the errors keep coming back. 

Anyone got a clue about how I can get this working?

I am also having issues with Mozilla Firefox not loading pages over https too, but I think I can describe that in another post :) 

Regards
Daniel

---

