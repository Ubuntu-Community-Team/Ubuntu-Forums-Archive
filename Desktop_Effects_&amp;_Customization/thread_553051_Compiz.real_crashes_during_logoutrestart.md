---
title: "Compiz.real crashes during logout/restart"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by Hyperkill on 2007-09-17
After getting compiz up and running really nicely I have a problem whenever I log out, switch user, restart, etc.  The desktop freezes but my AWN icon tray is still there including parts of my wallpaper.  At this point I can't really do much of anything except hold the power button down to shut down that way.

I noticed that when I kill the process of compiz.real in the systems monitor that the same problem occurs.  This leads me to believe that this is the culprit.

If anyone has any solutions it would be much appreciated.

---

### Post by smartboyathome on 2007-09-17
Try switching to metacity by using metacity --replace in a terminal, and see if it still freezes. It could be your comp freaking out about no WM.

---

