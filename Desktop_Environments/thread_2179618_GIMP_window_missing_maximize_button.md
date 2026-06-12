---
title: "GIMP window missing maximize button"
date: 2013-10-09
forum: Desktop Environments
---

### Post by frisket on 2013-10-09
Suddenly my main GIMP image window is taller than the screen (runs off the bottom) and it's missing the maximise (square) button. The button is there for a split second when the program fires up, but then it disappears, leaving only the X and the &#8211; buttons present. When I right-click on the window title bar, the Maximize function is greyed out and the Resize function only allows resizing the width. If I try to grab to top window edge, it won't drag down to resize the window. I have reinstalled it, but no change. 

All other applications work normally: only GIMP shows this behaviour, I have failed to find anything in the Preferences. Has anyone else seen this, or know how to fix it.

GIMP 2.8.4 under Ubuntu 13.04

[update] Completely removed GIMP (using Synaptic) and reinstalled and rebooted, and the problem is still there.

---

### Post by frisket on 2013-10-09
Aha. Turns out that Single Window Mode (where images are opened in tabs) prevents the window being resized vertically. I have no idea how is got into Single Window Mode, probably some random brush-over of the mouse (except that I have never used the Window menu). Unclicking Single Window Mode returns to normal behaviour.

This is probably a bug.

---

### Post by monkeybrain20122 on 2013-11-27
Actually you can resize witndow in single window mode. Switch to single window mode, go to Edit > Preferences > Theme and change "default ..." to "small .."

---

