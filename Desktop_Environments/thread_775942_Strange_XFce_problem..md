---
title: "Strange XFce problem."
date: 2008-04-30
forum: Desktop Environments
---

### Post by MotherMayI on 2008-04-30
I just did a fresh install of Xubuntu, and everthing went fine. I restarted to install my nVidia drivers and now there appears to be a problem with th way Xfce is handling windows.

Basicly, every time I boot up and enter an Xfce session it places a firefox window and two terminals up flush with the top left hand corner of the screen. These windows cover up the top bar (I have mine on autohide) and do not show up in the bottom taskbar. I also cannot move them or resize them in any way. 

Also, when I close the original windows and open any new ones (no matter what they are) they appear in the exact same place and with the exact same problems (cant resize, move etc.).

How can I get rid of them, and stop them appearing after every boot?

---

### Post by vambo on 2008-04-30
Seems as if xfwm isn't being started. Try the following.
Bring up Run Program - <alt> <F2>
Run xfwm4
Make sure you have "Save Session for Future Logins" enabled.

This should clear everything, both now and for future logins.

---

### Post by MotherMayI on 2008-04-30
Thanks a lot, worked perfectly.

---

