---
title: "CF_Installer-Updater_v.3.sh HELP PLEASE"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by amyfan on 2007-08-25
i used CF_Installer-Updater_v.3.sh to install compiz fusion and update it too but now i cant get it to remove everything it installed cause it dont work i do the uninstall but it wont work still theres none of the compiz or fusion installed in synaptics i tried term but nothing any one please help i dont want this crap in my comp if it dont work

---

### Post by hyperair on 2007-08-25
First of all, compiling software is something that an unexperienced person should never try. There is bound to be some sort of complication along the way.

Secondly, here's how to remove it: Go to this folder in your terminal: ~/compiz (~ means your home folder). In each of the subdirectories in that folder, open a terminal (this functionality can be gotten from nautilus-open-terminal in Synaptic), and type "sudo make uninstall". That should remove everything.

---

