---
title: "gnome panels empty and not responding"
date: 2009-11-15
forum: Desktop Environments
---

### Post by papaja1992 on 2009-11-15
Hello,

I'm using pure ubuntu 9.10. I've got the following problem. I was playing with my panels, and added a hiding one to the top to add some icons to it. 

Unfortunately both the default top panel (the one with tray and menu) and the new one became hidden and when I put cursor near the edge both of them went visible and right then invisible again. I was trying to click them with right button, and I got to the properties menu of panel. 

Unfortunately the window stopped responding. I closed it, rebooted, and now I have one top panel, one bottom panel with nothing on them. Neither left-click nor right-click shows any reaction. The same situation when logging into failsafe GNOME. 

I've explored all gnome folders in my home directory and found nothing interesting (no configuration files mentioning position or other atributes of panels). 

I was thinking of reinstalling/reconfiguring gnome-panel to overcome this, but netroot shell is not actually connected even if I am in the range of my wifi network. 

Do you have any ideas how to bring responding panels back to my desktop?

---

### Post by utnubuuser on 2009-11-15
Don't know about reinstalling them, but to restore them to their factory settings:> [http://ubuntuforums.org/showthread.php?t=1060406]("http://ubuntuforums.org/showthread.php?t=1060406")

and have your tried  Alt+F2 >> sudo killall gnome-panels

---

### Post by papaja1992 on 2009-11-17
Thanks, it worked. 

Funny thing is that my first thought was to replace my conf files with ones from LiveCD or something, but I didn't knew which they were. It turned out that removing all of them brought my panels back (even though I lost all appereance settings). I shouldn't have messed up with uninstalling and then installing gnome-desktop, because I've ended up with all the software I had removed earlier :( Playing with panels is not something you should try if you've already personlised your desktop. 

Anyway I can again use the system normally. Thanks!

---

