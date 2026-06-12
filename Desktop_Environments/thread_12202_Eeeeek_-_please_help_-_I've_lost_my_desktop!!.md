---
title: "Eeeeek - please help - I've lost my desktop!!"
date: 2005-01-22
forum: Desktop Environments
---

### Post by marcadams on 2005-01-22
Hi everybody;

I am in a bit of trouble, and as I am a noob with LInux, I am unsure how to resolve it.

I just uninstalled the Gnome Epiphany browser and Evolution, and when I rebooted all I see is my desktop wall paper. I don't have any top or bottom user bars.

The only thing I can do is right-click on the desktop and open a terminal, from which I can launch my FireFox web browser (so I can type this...)


I would be VERY grateful if someone can tell me what I have to do to restore my GUI desktop. 

FYI I am logged in, and thro' the command line can lauch nautilus and view my docs etc, so I think it is just a matter of the GUI.


Thanks for all you help
Marc

---

### Post by Perfect Storm on 2005-01-22
Try to install the packages you removed

sudo apt-get install epiphany-browser
sudo apt-get install evolution

reboot and see if it brings back the panels (I doubt it but try)



.:=The AI Dude=:.

---

### Post by ilari on 2005-01-22
[QUOTE=marcadams]Hi everybody;

I am in a bit of trouble, and as I am a noob with LInux, I am unsure how to resolve it.

I just uninstalled the Gnome Epiphany browser and Evolution, and when I rebooted all I see is my desktop wall paper. I don't have any top or bottom user bars.

The only thing I can do is right-click on the desktop and open a terminal, from which I can launch my FireFox web browser (so I can type this...)


I would be VERY grateful if someone can tell me what I have to do to restore my GUI desktop. 

FYI I am logged in, and thro' the command line can lauch nautilus and view my docs etc, so I think it is just a matter of the GUI.


Thanks for all you help
Marc[/QUOTE]
 Your desktop is missing only gnome-panel, but otherwise it should be Ok. In Ubuntu-linux gnome-panel is dependent of evolution-data-server that you've possibly removed (and thus gnome-panel is also removed, or it is not functioning correctly). Just re-install evolution-data-server (and also gnome-panel if missing). In my opinion synaptic is a good tool to check which packages are installed in your Ubuntu system.

---

### Post by marcadams on 2005-01-23
Few.....thanks ilari;

I've reinstalled the Gnome Panel..and all is well again in Linux land.

Thanks for the quick response !!
Marc

---

### Post by J. S. Jackson on 2005-01-23
LOL! I did the same thing, like 4 hours after installing Warty for the first time.  I was like  - UH OH!?  8-[ 

Well I saw someone with the signature:  "I know enough to get myself INTO trouble, but not enough to get OUT."  Well that fits me to a T.

---

