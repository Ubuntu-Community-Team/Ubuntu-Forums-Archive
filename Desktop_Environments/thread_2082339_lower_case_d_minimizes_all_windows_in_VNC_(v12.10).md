---
title: "lower case d minimizes all windows in VNC (v12.10)"
date: 2012-11-09
forum: Desktop Environments
---

### Post by wsblack on 2012-11-09
So I have been fighting this issue for an hour and a half now. I went through all of the posts that have been logged on the issue (about 10 in all) and while they got me closer, none of them solved for the issue.
 
I finally went to Applications -> System Tools -> Dconf Editor 
And then stepped through each of the trees until I found org.gnome.desktop.wm.keybindings
 
Now the trick here is that I thought by adding something in the keyboard shortcuts under preferences was somehow overwriting this field. It simply added what I had typed in so mine looked like ['<Primary>Down','<Primary><Super>d','<Super>d']
 
Both of the settings referencing 'd' didn't show up in the shortcuts list. I whacked the second and third setting keeping only '<Primary>Down'
 
That fixed it up for me. Hope that hour and a half saves some sanity points for someone else.
 
K

---

### Post by theronk on 2013-02-15
Thank you so much for this, the other threads about this issue don't have the resolution and this had also been driving me crazy.

---

