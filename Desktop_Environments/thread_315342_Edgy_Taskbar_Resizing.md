---
title: "Edgy Taskbar Resizing"
date: 2006-12-09
forum: Desktop Environments
---

### Post by jyotishman on 2006-12-09
Hi,

I am a newbie to Ubuntu Edgy and one of the things that is annoying me is automatic resizing of the taskbar (or window list, however it may be referred as) when one of the existing application windows has a long title its titlebar.

I believe the following link also suggests something similar:

[http://gnomesupport.org/forums/viewtopic.php?t=11903](http://gnomesupport.org/forums/viewtopic.php?t=11903)

The patch mentioned in the above discussion is already part of Edgy (libwnck18). I am not sure how I can fix this issue -- your help will be appreciated. 

Thanks,
- Jyoti

---

### Post by Dave54 on 2006-12-09
Just to the left of the window list should be a gray area or a bunch of dots. Right-click on it, and click Preferences. Select the Size tab. Adjusting these values may achieve the effect you're looking for.

Hope this helps!

-Dave

---

### Post by jyotishman on 2006-12-10
Thanks a bunch Dave -- this is exactly what I was looking for; didn't knew it would be this simple though :)

Cheers,
- Jyoti :)

---

### Post by Dave54 on 2006-12-10
You're welcome Jyoti

I have been trying to create a different effect, but it seems these settings can't reproduce it. Basically I want the window list to resize the same way it does in Windows. I have a maximum window list size of 1000px, however I want each window title button to stay at 200px, until I have more than 5 windows (5*200px=1000px max) in which case the window title buttons will scale down to fit the max window list size of 1000px.

Any ideas are welcome.

Thanks
-Dave

---

### Post by tweedledee on 2006-12-29
> **Dave54 said:**
> You're welcome Jyoti

I have been trying to create a different effect, but it seems these settings can't reproduce it. Basically I want the window list to resize the same way it does in Windows. I have a maximum window list size of 1000px, however I want each window title button to stay at 200px, until I have more than 5 windows (5*200px=1000px max) in which case the window title buttons will scale down to fit the max window list size of 1000px.

Any ideas are welcome.

Thanks
-Dave

See this post: [http://www.ubuntuforums.org/showthread.php?p=1944230#post1944230](http://www.ubuntuforums.org/showthread.php?p=1944230#post1944230).  Basically, you can't do it in Gnome, but KDE and XFCE have this behavior.  To keep Gnome but get this behavior, you can install the XFCE panel and use that as your taskbar instead of Gnome's panel (while still keeping your Gnome panel(s)).

---

