---
title: "Messing with KDE startup scripts"
date: 2007-04-07
forum: Desktop Environments
---

### Post by tophat_grendel on 2007-04-07
I recently installed Beryl on my machine, but took it off because it was acting too buggy. I then downloaded Compiz, which isn't working at all, and now KDE hangs every time I log in. I think it has something to do with the line I added to start Beryl automatically at log-in, but I have no idea how to remove the line without the GUI. Do I make a copy of the start-up file, remove that line and replace them? I have almost no knowledge of the command line, but I can use it if I know what to do. Thanks in advance.

---

### Post by tophat_grendel on 2007-04-08
I got it figured out. I feel stupid, but all it took was booting into recovery mode and typing ```
sudo apt-get install remove compiz-core
``` then ```
sudo apt-get autoremove
``` just for good measure. ```
shutdown -r now
``` to reboot, and KDE now boots without hanging, but still no Compiz. :(

---

### Post by tophat_grendel on 2007-04-09
Okay, I feel a bit stupid now. But in my defense, I couldn't fix this completely like I did without being able to use the GUI. If anyone else needs to delete a start-up link in KDE, and you can get into the GUI, the directory is: ```
/home/*username*/.kde/Autostart
``` then just trash the little gear thing you didn't want. I suppose if you needed to do it from the command line it would be: ```
rm /home/*username*/.kde/Autostart/*nameoffile*
``` Yes?

---

