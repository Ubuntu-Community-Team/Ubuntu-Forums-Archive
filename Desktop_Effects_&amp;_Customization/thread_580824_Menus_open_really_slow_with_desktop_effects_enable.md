---
title: "Menus open really slow with desktop effects enabled on 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by MegaSvensk on 2007-10-19
Hi,

I upgraded to 7.10 last night and since then the menus have become unresponsive when I've enabled the desktop effects (both effect levels.) It takes like a second from when a menu has been pressed until the menu pops up.

Before I upgraded, the desktop effects were not noticably slower when they were enabled than when they were disabled. The problem that kept me from using them then was that there was tearing in any videos I played. I was hoping that that had gotten fixed with this version but apparently it just got worse.

My PC specs are:
AMD Athlon 64 3500+ @2.2 GHz
2 GB DDR RAM
GeForce 7600GS

---

### Post by Nicksha on 2007-10-19
If you have two screens, there are others with the same issue:

[http://ubuntuforums.org/showthread.php?p=3567436](http://ubuntuforums.org/showthread.php?p=3567436)

For me, the problem goes away when the second display is turned off (but I wouldn't call that solution).

---

### Post by MegaSvensk on 2007-10-19
Thanks for your reply. But I cannot turn of the second screen because I use it all the time.

---

### Post by Nicksha on 2007-10-19
[This page]("http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=2") has some info. Maybe, like they described, you can just disable compiz on the second monitor. It worked for me.

---

### Post by MegaSvensk on 2007-10-19
Okay, sounds good, at least for a temporary solution. 
It says I'm supposed to add these lines to my session. How do I do that?
```
#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &
```

---

### Post by Nicksha on 2007-10-19
You should copy those lines to a text file, and save it (I don't think it matters where you save it or how you name it; I usually put scripts in /home/username/bin folder). Make it executable (right click the file > properties > permissions and there check the checkbox that allows the execution). Then, run gnome-session-properties, and add the script there. I think that's about it.

I think the idea is to turn off all visual effects in the gnome-appearance-properties, and then this script will enable them on login for the first screen only.

---

### Post by MegaSvensk on 2007-10-19
Thank you. I did what you said and now the interface feels even more responsive than without the effects.

---

