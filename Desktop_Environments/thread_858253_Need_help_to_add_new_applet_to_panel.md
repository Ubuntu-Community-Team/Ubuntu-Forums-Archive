---
title: "Need help to add new applet to panel"
date: 2008-07-13
forum: Desktop Environments
---

### Post by stormtrooprdave on 2008-07-13
I can't figure out how to add this applet to the panel.  I downloaded gnetload from [here]("http://www.gnomefiles.org/app.php/Gnetload") and have extracted it on the desktop but I don't know how to add it on to the panel.  This is probably a simple thing but I'm new to this.

---

### Post by Tim Sharitt on 2008-07-13
The file you pointed to is the source code, it has to be built and installed before it can be installed. First make sure all of the dependencies listed on the site are installed, specifically the dev files (ex. for gtkmm it would be libgtkmm-dev or something similar in synaptic).
Next open a terminal and enter the following:
```
./configure --prefix=/usr
make
sudo make install
```
Next, restart gnome-panel (or just log out and back in) and you should be able to add it.
Note: configure may fail with unsatisfied dependencies not listed. The easiest thing I can tell you is to install the missing files until you no longer get the errors.
One more thing, each of the steps listed in the code block above take a little while to finish.

---

