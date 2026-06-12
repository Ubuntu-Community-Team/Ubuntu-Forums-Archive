---
title: "startx in Ubuntu 9.10 (Karmic)"
date: 2010-03-14
forum: Desktop Environments
---

### Post by goldragon83 on 2010-03-14
The other day, I was thinking about installing KDE on my ubuntu computer, 9.10. I thought that maybe KDE was already installed and all I had to do was logout and switch, so I logged out. There were options at the bottom of the screen to either startup in GNOME, or to use this other thing...It had an x in it. I don't remember exactly what it was because I can't get back into GNOME to check. Anyway, now whenever I startup Ubuntu 9.10 it only comes up with a terminal at the top left of the screen. I tried using the command "startx" thinking that it could help, but I got the error 
"user not authorized to run the x server, aborting".
I am very, very new to linux and don't understand much of it. I don't even know if startx is going to load GNOME. I read something about changing it so that "anybody" can use it instead of just root, but I was unclear about it. Is there a way to get GNOME working correctly before I made the switch? And if I need to login to root, how do I do that?
Thanks

---

### Post by Babuloseo on 2010-03-14
i am a newbie too... try doing sudo su and then using startx

---

### Post by asmoore82 on 2010-03-14
As you are logging in, switch it back to GNOME at the bottom.

This "other" session should be a super-old-school "xterm."

---

