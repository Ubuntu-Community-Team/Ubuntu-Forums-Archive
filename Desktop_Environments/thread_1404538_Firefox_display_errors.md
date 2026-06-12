---
title: "Firefox display errors"
date: 2010-02-11
forum: Desktop Environments
---

### Post by MJBoa on 2010-02-11
Hey guys,

So I'm having annoying errors with firefox. I am getting strange rendering issues with the windows. It's usually popups and drop down menus. Specifically, the bookmark dropdown options and some options for extensions like Tab Mix Plus. Buttons change width and boxes that aren't selected look like they are and there are just general oddities. 
I attached a picture of the bookmark dropdown. If you look at the list of folders where I can put the bookmark, you'll notice the scroll bar is at the bottom but it looks like the list is at the top. I can't see past the top of the list and nothing changes when I select the folders. And obviously, the options at the top disappeared. I CAN select them but it's just the display that's messed up.

I already tried changing xorg.conf by adding
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
to device and screen but it didn't help.

I can always go to the bookmarks manager but this is getting annoying. I had these errors on 9.04 too but it was less pronounced.
Thanks for any help you can give.

---

