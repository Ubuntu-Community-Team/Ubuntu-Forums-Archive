---
title: "Gnome screensaver inhibitor + launcher help"
date: 2009-03-29
forum: General Help
---

### Post by nssone on 2009-03-29
Hey there guys, trying to get a little help. I have DOSBox installed with a shortcut on my panel. My problem is when running DOSBox, the screensaver still kicks in after a while. After much searching, I finally found this old post here [http://ubuntuforums.org/showthread.php?t=442569](http://ubuntuforums.org/showthread.php?t=442569) The problem is I can't figure out how to implement that into the panel launcher, including the killall command. Any ideas? Thanks in advance.

---

### Post by PhrankDaChickenGeek on 2009-03-29
Open gedit and save the folling as start_dosbox.sh

```

#!/bin/sh

#Disable Screensaver
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool FALSE

# Start DOSBox
dosbox

# Enable ScreenSaver when dosbox closes
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool TRUE

```

Make it executable:
```
chmod a+x start_dosbox.sh
```

Then create an new "Custom Application Launcher" on a panel that points to start_dosbox.sh

---

