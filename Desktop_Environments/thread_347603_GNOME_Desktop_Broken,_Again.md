---
title: "GNOME Desktop Broken, Again"
date: 2007-01-27
forum: Desktop Environments
---

### Post by lakelovers on 2007-01-27
I'm probably breaking forum protocal because I posted this problem on the General Help forum but got no answers. I'm also embarassed because this is the third time my GNOME has gone haywire. I can get to the sign-in screen and GNOME starts but when the desktop is supposed to appear, I get white bars top and bottom, nothing in between except color. Here's what I've tried: "sudo aptitude update;" then  "sudo aptitude upgrade," and also "sudo aptitude update;" then "sudo install ubuntu desktop." The latter ended with "Need to get OB of archives. After unpacking OB will be used." I don't know what OB, is or where to go from there. (I was perusing "Themes" when I lost the desktop.) Please help.

---

### Post by Dr. Nick on 2007-01-27
0b is actually "zero bytes" meaning that nothing needs to be downloaded.

If you were playing with themes then it probably goofed something up, Quickest possible fix would be to login to a failsafe gnome or failsafe terminal from the gdm screen and then rename the .gconf and .gnome2 folders to something like .gcongbak and .gnome2bak and then on restart the gnome settings will be reset. If you find a solution it would be best to add the link to the other thread just incase someone finds it and not this one in the future


A fellow East Texan lol

---

### Post by lakelovers on 2007-01-27
Thank you, thank you, Dr. Nick. I renamed .gconf and .gnome2 and got the GNOME desktop back pretty much. I say "pretty much" because the top panel did not have the various launch icons on it. I added the icons but when I rebooted, the icons were gone, and needed reloading. So, something not quite right but except for that minor glitch, everything seems ok.

---

### Post by Dr. Nick on 2007-01-27
renaming them 2 folders resets gnome back to defaults for the most part, I had you rename them instead of delete just in case it wasnt the problem you would have lost your custom config un-needlessly 

Glad it is almost back to wroking.

---

