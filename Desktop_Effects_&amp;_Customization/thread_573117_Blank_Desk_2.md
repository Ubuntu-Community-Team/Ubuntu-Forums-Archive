---
title: "Blank Desk 2"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by wahoobob on 2007-10-11
I have a problem with Gutsy that the desk 2 comes up blank and no controls to switch back.  Any ideas?

---

### Post by indecisive on 2007-10-11
The blank screen is most likely because Ubuntu has started Compiz Fusion, but your computer can not support Compiz Fusion at the default depth, 24.  To change your default depth to 16, which will most likely work for you, so you can either keep or remove Compiz Fusion, do this:

1.  Press Ctrl+Alt+F6
2.  Enter this command: *sudo nano /etc/X11/xorg.conf* (you will need to enter your administrative password)
3.  Scroll down to the Screen section and change the DefaultDepth number to 16.
4.  Press Ctrl+X to save and quit.
5.  Either reboot by entering *sudo reboot* (again, only administrators can shutdown or reboot a system via the terminal) or press Ctrl+Alt+Delete to restart X11 and Ctrl+Alt+F7 to return to graphical mode.
6.  Log in and Compiz Fusion should work!  If you do not want to keep the depth at 16, under the Visual Affects tab of the Appearance window (System => Preferences => Appearance), disable Compiz Fusion and use the above steps to reset the DefaultDepth to 24.

---

### Post by wahoobob on 2007-10-11
I changed the depth to 16 and it still does the same thing.  I checked the depth to make sure it changed.  the screen only shows my wallpaper image and no controls.  I have to reboot to get to the first screen.  Is there a way to change to only one screen? or to try changing the number of screens?

---

### Post by indecisive on 2007-10-11
It would appear as though your computer will not support Compiz Fusion in any depth.  If you want to disable Compiz Fusion: 

1.  Enter a terminal (Ctrl+Alt+F6) and enter "ps -ef | grep compiz" to show the Compiz Fusion thread.

2.  Find the PID (Process ID) of the thread.  It should be the first number listed, but to confirm, run just "ps -ef" to see the column labels

3.  Run "kill -15 [PID you found]"

4.  Re-enter the X11 (Ctrl+Alt+F7)

This should terminate Compiz Fusion so you can use the instructions I gave before to disable it.

---

### Post by wahoobob on 2007-10-11
Instead of killing compiz fusion, and since I seldom use to work areas, I went back to 24 depth, turned off screen effects for a moment, changed to one work area, removed the switcher from my bar and then turned the effects back on.  They work fine in one screen.  Maybe the final version of Gutsy will address this problem since I see other questions about it.

thanks for the ideas.

---

