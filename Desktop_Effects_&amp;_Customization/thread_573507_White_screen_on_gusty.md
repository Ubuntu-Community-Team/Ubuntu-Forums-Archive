---
title: "White screen on gusty"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by thoman on 2007-10-11
Hi all

Iam testing 7.10, upon testing special desktop effect seeting my screen turn into white screen with a cursor only blinking, how do i revert to the old setting???:confused:

---

### Post by indecisive on 2007-10-11
The blank screen is most likely because Ubuntu has started Compiz Fusion, but your computer can not support Compiz Fusion at the default depth, 24. To change your default depth to 16, which will most likely work for you, so you can either keep or remove Compiz Fusion, do this:

1. Press Ctrl+Alt+F6
2. Enter this command: sudo nano /etc/X11/xorg.conf (you will need to enter your administrative password)
3. Scroll down to the Screen section and change the DefaultDepth number to 16.
4. Press Ctrl+X to save and quit.
5. Either reboot by entering sudo reboot (again, only administrators can shutdown or reboot a system via the terminal) or press Ctrl+Alt+Delete to restart X11 and Ctrl+Alt+F7 to return to graphical mode.
6. Log in and Compiz Fusion should work! If you do not want to keep the depth at 16, under the Visual Affects tab of the Appearance window (System => Preferences => Appearance), disable Compiz Fusion and use the above steps to reset the DefaultDepth to 24.

---

