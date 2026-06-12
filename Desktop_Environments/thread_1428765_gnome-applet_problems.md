---
title: "gnome-applet problems"
date: 2010-03-13
forum: Desktop Environments
---

### Post by nikefalcon on 2010-03-13
Hi folks
I clicked on the gnome-applet in the top right corner(FastUserSwitchApplet(?)) and clicked on 'suspend' instead of 'lock screen'.I thought I had clicked outside and clicked on 'lock screen'; the screen went blank,and i saw the password prompt to unlock screen,but before i could do anything, the system powered down.So I pressed the power button, and after some time I was asked for the password to unlock screen.When i entered the password the system froze.Then, I reset the system,but after logging in got the following message:
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?

i tried rebooting and reinstalling gnome-panel,gnome-panel-data; with no effect.
I even tried restoring the panels to the default configuration but i get the same error message.
Please help me to get the applet back.

thanks,

---

### Post by %rm on 2010-05-29
I have the same error message with several other applets as well:

ClockApplet, IndicatorApplet, NotificationAreaApplet, WorkspaceSwitcherApplet, Panel_ThrashApplet, WindowListApplet, ShowDesktopApplet

Additionally the panel seems to restart and throw again the error messages whenever I try to add anything into the panel.  Bottom panel is empty and totally useless.  Tried all kinds of panel and gnome restarts and reinstalls but nothing seems to help.

Should I reinstall Ubuntu 10.04 altogether?  Or downgrade back to 9.something?

---

### Post by PA28 on 2010-06-06
Try renaming the "panel" folder in /home/<user>/.gconf/apps/ to "panel_backup", and logout and back in again.

I messed up my panel applets and this method restored everything to their defaults again. I'm hoping with a bit of luck it may fix your issue too...

---

### Post by %rm on 2010-06-06
Renaming did not help.  I even created a new user without any customizations but the clock applet problem remained.  Some improvement is there though: recent ubuntu updates fixed the other applets I reported earlier, only the clock problem remains.

There is quite many gnome-panel bug reports in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel").

---

### Post by nikefalcon on 2010-10-04
Unfortunately I shall on longer be able to support this thread as I have upgraded to Lucid(via clean install).
#-o
Thanks for your support.

---

