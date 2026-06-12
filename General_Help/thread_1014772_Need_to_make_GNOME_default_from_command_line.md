---
title: "Need to make GNOME default from command line"
date: 2008-12-18
forum: General Help
---

### Post by geoff511 on 2008-12-18
After un-installing a KDE download manager, Ubuntu now starts at the command prompt.

Have tried the command -
sudo /etc/init.d/gdm start
and I get the response -
"not starting GNOME display manager - not default display manager"

Anyone know the command to make GNOME the default display manager from the command prompt ?

Thanks

---

### Post by bigbrovar on 2008-12-18
I had that problem before. it happens when you choose kdm instead of gdm as your default while installing kubuntu-desktop. what i usually do is to remove kdm completely ```
sudo apt-get remove --purge kdm 
``` then i also remove gdm ```
sudo apt-get remove --purge gdm
``` then i reinstall gdm ```
sudo apt-get install gdm 
``` maybe not the best solution out there but it always works for me.

---

### Post by geoff511 on 2008-12-18
You are a life saver bigbrovar !!!
Who cares if it's not the best way to do it -- it worked !!

Once again thank you very much.

---

