---
title: "The Magical DIsappearing Desktop Background"
date: 2008-12-02
forum: General Help
---

### Post by derklempner on 2008-12-02
I've seen many threads on this issue, and a day after reinstalling Ubuntu on a "new" computer, the same issue happened to me:

***The desktop background picture disappeared, is now set to the default color, and you are unable to change the desktop background to anything other than a solid color; it will simply not load a picture.***

When this issue arose for me, I immediately thought of VNC's ability to remove the desktop background when remote connections are made to the system in question.  I hoped that it was just a VNC connection that had ended "poorly" and caused GNOME to not restore the selected background image.  The fix was simple: make another VNC connection to the system and then disconnect.  The wallpaper reappeared immediately.

I'm writing this to possibly help others with the same issue.  So if you've made a remote desktop connection to your Ubuntu system and the wallpaper disappears, give this a try and see what happens.

---

