---
title: "Xubuntu 7.10 Menu Bar disappeared"
date: 2007-11-09
forum: Desktop Environments
---

### Post by batbuntu on 2007-11-09
The top menu bar (the control bar at the top of the screen with the clock and applications menu), and the bottom status bar have disappeared.

I was playing freecell, which froze. I logged out. When I logged back in the bars were gone. They're still gone after a reboot.

I found a thread ([http://ubuntuforums.org/showthread.php?t=312394](http://ubuntuforums.org/showthread.php?t=312394)) suggesting starting xfce4-panel in a command window, and this does indeed restart the bars. Of course as soon as I close the command window the bars disappear again. Removing the panels.xml file didn't make any difference.

Is there any way to get the bars back, or is it reinstall time?

Thanks!

---

### Post by bharadwaj on 2007-11-10
yeah even i had the same problem but i don remember what happened but i was able to acces all other apps from my right click mouse menu. Later this problem was fixed when i formatted my HDD with Ubuntu ;) lol

---

### Post by Spin Doctor on 2007-11-10
Hey there, 

I experienced the exact same thing as you did when playing freeciv on my xubuntu 7.10 alpha release. The only thing I figured to do was to create a new user account to get back the meny. But I really did not try really hard to solve the problem since it was just a testinstallation. But if you run out of options - try creating a new user and migrate your documents and settings to that one.

---

### Post by vambo on 2007-11-10
> **batbuntu said:**
> The top menu bar (the control bar at the top of the screen with the clock and applications menu), and the bottom status bar have disappeared.

I was playing freecell, which froze. I logged out. When I logged back in the bars were gone. They're still gone after a reboot.

I found a thread ([http://ubuntuforums.org/showthread.php?t=312394](http://ubuntuforums.org/showthread.php?t=312394)) suggesting starting xfce4-panel in a command window, and this does indeed restart the bars. Of course as soon as I close the command window the bars disappear again. Removing the panels.xml file didn't make any difference.

Is there any way to get the bars back, or is it reinstall time?

Thanks!

Have you tried:

1. Make sure you have "save Session" selected
2. Start the panel in a terminal and in the background - xfce-panel &
3. Logout then back in **do not** kill the terminal you launched the panel from

---

### Post by batbuntu on 2007-11-10
Thank you Vambo!

Your suggestion worked:

1) Start xfce4-panel in the background.
2) Logout with Save Session enabled.

---

### Post by nemarona on 2007-11-25
I know this is solved, but I would like to point out that a simpler solution worked for me:

1) Uncheck "Save session"
2) Log out and log in again

I guess a default, empty session comes with xfce4-panel on...

---

### Post by V-600 on 2007-12-11
Sorry to dig up an old post but I can't seem to log out and in again. When I go to the quit button at the top right I just get the options to exit the xfce panel. There are none of the normal log out, shutdown or save session options.

Also what does it mean 
1) Start xfce4-panel in the background.

Thanks

EDIT: I booted into the recovery mode, ran the command "startx" then logged back out while saving settings. This seemed to fix it (unless it was something else i tried at the same time)

---

### Post by possumator on 2007-12-23
I Had the same problem of no taskbar or menubar. 
Unchecking save session and logging out didn't fix it.
However, opening up a terminal session and starting xfce4-panel did. 

thanks:-)

---

### Post by luxerama on 2008-02-18
Or you can just run:
```
xfce4-panel &
```
And then:
```
disown
```
closing the console now wont close the panel....

---

