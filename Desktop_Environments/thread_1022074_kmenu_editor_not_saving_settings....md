---
title: "kmenu editor not saving settings..."
date: 2008-12-26
forum: Desktop Environments
---

### Post by thisperishedmin on 2008-12-26
Hey guys, so for some reason my Virtual Box launcher in the KDE Menu has stopped functioning. I cannot trace it to any exact event, but I think it may have occurred after I copied the VirtualBoxManage script into /usr/bin to make some tasks a bit easier. Now, when I click the Sun xVM link in the menu, the program simply fails to launch.

Ive removed the entry in /usr/bin for VirtualBox manager tools, but still no luck.

If I open konsole and enter "/usr/lib/virtualbox/VirtualBox" the program loads as expected. Ive tried entering the KDE menu editor and dropping this in the command box, as well as in advanced under run in terminal. I would assume this should fix it, but the settings mearly wipe out next I go to look at it

Is that because im not launching the KDE Menu Editor with root privileges? If so - how can I open it with root priv?

Is there an alternative fix for this problem? This is the first time I've gotten stuck on a little nuisance problem and havent resolved it on my own in less than a few minutes tinkering in almost a year...I'm bummed haha


Thank you in advance for any suggestions or fixes!

---

### Post by thisperishedmin on 2008-12-26
problem solved through manual editing of /usr/share/applications/VirtualBox.desktop file.  I'm not sure what was wrong, but I configured it to the appropriate filepath (instead of only the shortened "VirtualBox") and removed some of the "filler" stuff from the file, and now the launcher works fine.

Still have no idea what boffed, but this resolved my problem.  I'm still unclear why I cannot edit the menu with the GUI tool but oh well. I tried to chown the /var/tmp/kdecache-<username> and the home KDE files and it did not help.  If anyone has experience with that I would still like to know what may help - but its not urgent now.

Thanks!

---

