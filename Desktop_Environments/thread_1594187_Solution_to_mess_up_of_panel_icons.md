---
title: "Solution to mess up of panel icons"
date: 2010-10-12
forum: Desktop Environments
---

### Post by ft-Orchard on 2010-10-12
Sometimes the icons in the panels are messed up. 
This is really annoying and a bug report and brainstorm are already created for this problem.

[http://brainstorm.ubuntu.com/idea/8079/](http://brainstorm.ubuntu.com/idea/8079/)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1239827.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1239827.html)

A solution to this problem was already found in:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1458265](http://ohioloco.ubuntuforums.org/showthread.php?t=1458265)
But this involves user actions. Also, the script kills gnome-panels and starts it up again. 
This could slow down your system when starting up. But I think its worth it!

An automated way to restore panel icons on startup goes as folows. 

Put this script in your favourite bin directory. (save as: savePanel.sh)
```

#!/bin/bash
savedDirectory="PUT HERE YOUR SAVE DIRECTORY"

gconftool-2 --dump /apps/panel > ${savedDirectory}/panel_saved.conf

```Then put this script next to it. (save as: restorePanel.sh)
```

#!/bin/bash 
savedDirectory="PUT HERE YOUR SAVE DIRECTORY"

gconftool-2 --load ${savedDirectory}/panel_saved.conf
killall gnome-panel

```Run the following line of code:
```

$ cd %YOUR BIN DIR%
$ chmod +x *Panel.sh

```(replace %YOUR BIN DIR% with the scripts bin dir!)

The first script will save your panel configuration, the second will restore it from the saved file. Now we need to let these scripts run automaticly.

(replace %YOUR BIN DIR% with the bin dir the scripts are set in.
```

$ cd /etc/rc0.d
$ sudo ln -s %YOUR BIN DIR%/savePanel.sh K60savepanel
$ cd ../rc6.d
$ sudo ln -s %YOUR BIN DIR%/savePanel.sh K60savepanel

```The scripts are now runned at shutdown and restart. (init lvl 0 & 6)
Still, we need to run the restore script at startup. This must be done when starting up
the desktop, due to screen resolution.

Either, go to "Preferences > Startup applications", or type in terminal: "gnome-session-properties" and configure the restore script to startup. 

You can also put the following script in this directory /home/%YOUR USERNAME%/.config/autostart/

```

[Desktop Entry]
Type=Application
Exec=%YOUR BIN DIR%/restorePanel.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Restore_panel
Name=Restore_panel
Comment[en_US]=Restore panel icons.
Comment=Restore panel icons.

```(replace %YOUR BIN DIR% with the scripts bin dir!)

Now you're set.

ps. If someone has a better solution for the restore script, so, restore the panel another way, I'll be glad to read it!

---

### Post by ft-Orchard on 2010-10-12
Maybe this thread should be in:
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by steven_liauw on 2010-10-25
Great script!

When I tried it in the 10.04 Lucid, it works as is...
But when in 10.10 Maverick, the "killall gnome-panel" line in restorePanel.sh seems to kill the panel and not restart it.
So, the desktop became panel-less after running restorePanel.sh

To remedy it, I added an extra line after "killall gnome-panel" which is "gnome-panel"
That way, the panel is manually restarted

---

### Post by heavy metal on 2010-10-25
Was having same problem but fixed it by changing the default theme to clearlooks theme now panel icons do not go crazy anymore...:guitar:

---

