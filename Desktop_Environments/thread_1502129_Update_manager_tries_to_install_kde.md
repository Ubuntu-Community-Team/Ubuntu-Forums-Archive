---
title: "Update manager tries to install kde"
date: 2010-06-05
forum: Desktop Environments
---

### Post by Cederien on 2010-06-05
I've installed Gwenview (the old 1.4.2 version as the current version completely lacks the functionality I need) to my otherwise pure Gnome install, using only the minimal amount of KDE libraries. However update manager now tries to have me newly install 98 KDE packets every time it comes up (looks like pretty much the whole basic KDE desktop). The problem also extends to Synaptic, but not to apt. Any way to change this behavior?

---

### Post by Barafu Albino Cheetah on 2010-06-05
Did you install gwenview using "Ubuntu Software Center" Never use it for apps from another desktop system? 
No matter, remove gwenview, use any tool to remove orphaned packages, check if everything is OK now. Update, install gwenview with apt-get. 
Login to gwenview bugtrack and support the request to replace G with K. Sometimes traditions are better to be followed.

---

### Post by Cederien on 2010-06-05
Thanks, afraid though it didn't work out. Removing Gwenview also made update manager cease in his attempts to install KDE for me, but as soon as I add it again (I used dpkg instead of apt-get as Gwenview 1.4.2 isn't in the repositories anymore) the problem is back as well. :(

---

