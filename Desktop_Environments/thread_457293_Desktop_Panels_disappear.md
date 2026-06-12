---
title: "Desktop Panels disappear"
date: 2007-05-28
forum: Desktop Environments
---

### Post by rdcmmnst on 2007-05-28
I am a new user with Fiesty fawn.. I have enabled desktop effects and am extremely pleased with them. My only complaint is that when i send a window to a different workspace by clicking and dragging it into the workspace switcher located in one of my panels the window will move. but when i click on that desktop it will go there but the only thing there will be the window. None of the panels will be there. I can't right click on the desktop nothing..just the window. 

If i hit send to workspace right with the right click menu and then hit ctrl+alt and then right arrow key it works fine. 

If something doesn't make sense let me know. I'm not the best with descriptions. thanks

---

### Post by rdcmmnst on 2007-05-28
did i not give enough information?

---

### Post by rdcmmnst on 2007-05-29
bump..perhaps?

---

### Post by atrophic on 2007-10-03
I'm having the same problem on gutsy.  I have the Desktop Wall and Expo plugins enabled and I can switch workspaces fine with control-alt arrow keys, or by bringing up Expo, but if I actually click the switcher on the panel, all panels go away.  I can still switch between the workspaces, but there are no panels.

---

### Post by gregladen on 2007-10-11
I have the same or a similar problem.  I have Feisty Fawn installed with desktop effects turned on.  When I go to a new desktop (any and all of the three that are not number 1) there is no panel (the thingie normally along the top) and no taskbar.  When I click back to the first desktop, there is a pause, and I end up at the first desktop, and then everything reappears. 

The very first time this happened, there were no panels or taksbars anywhere.  I alt-ctrl-deleted out and signed back in and everything was there (on desktop 1) again, but the behavior continued.

Anybody got a fix or an idea?

Thanks

---

### Post by gregladen on 2007-10-11
Add the following to the "Device" section of xorg.conf

"Option "AddARGBGLXVisuals" "True" 

Here's how:

Back up xorg.conf first, in a terminal, like this:

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.mybackup

then edit the xorg.conf:

sudo gedit /etc/X11/xorg.conf

then scroll down to the section that starts like this:

Section "Device"

Then paste the following line into the section, perhaps at the end, bfore the "EndSection" line:

        Option "AddARGBGLXVisuals" "True"


If you mess this up or for some reason it does not work on your system, you will need to revert to backup.  If your Gnome and X system is totally fried, get yourself somehow to a terminal prompt and copy the backup file back over the xorg.conf file:

sudo cp /etc/X11/xorg.conf.mybackup  /etc/X11/xorg.conf

and then you could do:  

sudo startx 

or reboot or whatever seems to work.  Good luck!

I got this from here:

[http://ubuntuforums.org/archive/index.php/t-422935.html](http://ubuntuforums.org/archive/index.php/t-422935.html), posted by stoppeltje, and I have no idea why it works.  But clearly stoppeltje is our hero today.

---

