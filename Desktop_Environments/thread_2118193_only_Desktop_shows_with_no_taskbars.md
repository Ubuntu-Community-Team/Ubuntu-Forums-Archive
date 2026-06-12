---
title: "only Desktop shows with no taskbars"
date: 2013-02-20
forum: Desktop Environments
---

### Post by derick881 on 2013-02-20
I am running unbuntu 12.10 on an AMD64 desktop machine. This morning the software updater notified me of new updates available.  After downloading I performed the requested reboot.
Now all I get is my Desktop with only items I had on the desktop.  There is no bar on the top of the screen or shortcut icon bar down the left side of the screen.  I cannot get to any menus to look at anything.  The only thing that works is to right click on the Desktop and look at setting the wallpaper and other appearance settings.  One of the settings is to hide the bar on the left side of the screen but this is turned off.  Turning it on and off again does nothing.

I can get to general settings through this menu and eventually get a file menu and a firefox brouser through Ubuntu One settings.  Everything seems to be running in the background but no access to it.  I cannot even get a terminal up.

I see a couple of posts on this forum in the last few hours with similar complaints.  What did Ubuntu push downstream and what have they done?  I noticed in the download dialog something about downloading kernal xxxxx.xx.x.xx bla bla.  

where do I go from here?

---

### Post by Frogs Hair on 2013-02-20
Try Ctrl + Alt + T to open the terminal and paste the following Command.

 ```
setsid unity
```

---

### Post by tadis on 2013-02-21
Try updating kernel:
```
sudo apt-get install linux-headers-$(uname -r)
```

I fixed same problem (today) by reinstalling ubuntu-desktop:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

