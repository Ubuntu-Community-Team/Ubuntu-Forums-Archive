---
title: "font rendering"
date: 2005-07-08
forum: Desktop Environments
---

### Post by art on 2005-07-08
Hi forum
I installed KDE on my Ubuntu, but then didn't quite like it, and did 

sudo apt-get remove kdelibs4 libqt3c102-mt arts

  Well, KDE is gone now, but I guess I have played with fonts while in KDE and somehow the settings in GNOME for regular user now are screwed. In root account they are fine. For example if I change font rendering from Best Shapes to Monochrome in root account I see difference, in user account nothins happens. 
  Anyone knows how can I get the old fonts settings back, or which file holds these settings for root so that I just copy them for the regular user. 
Thanks a lot!

---

### Post by art on 2005-07-09
It turned out KDE has created a hidden fonts config file, removing which solved the issue.

---

