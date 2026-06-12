---
title: "Beryl vs Feisty"
date: 2007-04-20
forum: Desktop Environments
---

### Post by d2843 on 2007-04-20
I had Beryl working great in Edgy, but in Feisty it won't render the window borders. I'm using Nvidia.

---

### Post by Sqwishy on 2007-04-20
Check that you have the correct things in your xorg.conf
So from the terminal...
sudo nano /etc/X11/xorg.conf
Then look for... Section "Screen" 
Under that, add...        Option "AddARGBGLXVisuals" "True"
Unless it's already there, but it probobly isn't. Adding that and restarting X should fix it :D

---

### Post by netcyrax on 2007-04-21
The "AddARGBGLXVisuals" option should be added in the Device section according to the 
[Beryl FAQ]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631")..

Anw, done that, reload X and the problem was solved for me! :)

---

