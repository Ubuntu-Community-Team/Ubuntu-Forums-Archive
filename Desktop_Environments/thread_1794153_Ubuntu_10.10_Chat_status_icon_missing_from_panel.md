---
title: "Ubuntu 10.10 Chat status icon missing from panel"
date: 2011-06-30
forum: Desktop Environments
---

### Post by Slench on 2011-06-30
I'm not quite sure what it's called, but it's the one with the speech-bubble next to my account name... 
I've looked everywhere, but because I don't know what it's called I can't find it.

on the forum I can only find ways to get the mail icon back...

so.. any ideas?

---

### Post by Krytarik on 2011-06-30
This is part of the "Indicator Applet Session", this also includes the power button with the session options. So, first make sure that it is added to the panel. If so, but the, say, status indicator still isn't there, make sure that the package "indicator-me" is installed:
```
dpgk -l |grep indicator-me
```If it doesn't show up there, install it with:
```
sudo apt-get install indicator-me
```Or you can also try reinstalling it:
```
sudo apt-get install --reinstall indicator-me
```If you had to install it, relogin thereafter or restart Gnome Panel with:
```
killall gnome-panel
```Greetings.

---

### Post by Slench on 2011-06-30
oh...

see.. the power button disappeared earlier today, and I found that to bring it back I had to add the indicator applet session...
thereby assuming it ONLY added the power button...
because I couldn't move the icons around, I had to delete the one with the speech bubble... So by assuming that it only brought back the power button icon, I had no idea...

thanks for the help!

---

