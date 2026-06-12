---
title: "Resolution problems"
date: 2006-04-15
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-15
Hey. When setting up my Ubuntu installation I setup my screen resolutions incorrectly. I accidentally set my resolution larger than 1024x768 (1024x768 is my optimum resolution). Anyway, when I log in I changed the resolution back to 1024x768, but when I rebooted and was at the log-in screen, the resolution was larger than 1024x768, how do I fix this?

---

### Post by Ramses de Norre on 2006-04-15
sudo gedit /etc/X11/xorg.conf
Find the lines with all the resolutions and add your favorite resolution as first to all of those lines.

---

### Post by Bloch on 2006-04-15
Run 
 sudo dpkg-reconfigure xserver-org

This program reconfigures your xorg.conf file. It creates a new xorg.conf and your old one will be xorg.conf_backup

You will need to restart X to see the effect. (ctr; alt backspace)
If you are happy with the result, fine. Or you might like to compare the old and new .conf files, and if the old one worked fine for you, only add the changes that concern the resolution. Just make sure you always have a backup.

---

### Post by Elrohir on 2006-04-16
and if I get this (look at attachment) error???

---

