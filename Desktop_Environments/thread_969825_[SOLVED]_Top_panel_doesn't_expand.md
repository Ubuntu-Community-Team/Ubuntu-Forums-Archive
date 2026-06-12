---
title: "[SOLVED] Top panel doesn't expand"
date: 2008-11-03
forum: Desktop Environments
---

### Post by Nevon on 2008-11-03
After changing my desktop resolution from 1152x864 to 1440x900 my top panel refuses to expand all the way to the right. I'm guessing that it's still at 1152px width. I've tried restarting X, restarting my computer, deleting and then re-creating it, but nothing has worked.

I've attached a screenshot where you can see what it looks like. 

Any ideas?

---

### Post by steveydoteu on 2008-11-03
Is it set to expand?

---

### Post by Tamlynmac on 2008-11-04
Right Click on panel and select properties - check Expand if not checked.

---

### Post by Nevon on 2008-11-04
> **steveydoteu said:**
> Is it set to expand?

Yes. It's set to expand.

---

### Post by Tamlynmac on 2008-11-04
Whats odd is your bottom panel is expanded probably by default. You may wist to check your gconf-editor to assure the top panel expand is actually selected (checked). You could also check the entire gnome setup between top and bottom panels in the editor..

gconf-editor/apps/panel/toplevels/top_panel_screen

---

### Post by Nevon on 2008-11-05
I checked gconf-editor, and the only difference between the top and bottom panel is that the top panel is said to be on screen 1, while the bottom panel is on screen 0. The weird thing is that I can't change the value for the top panel. Do I have to do it as root? Also, if I tick the buttom that says "mirror screen" or something like that in the application Screen Resolution, the panels look fine. But instead they sometimes just disappear off of the screen when I'm using Firefox. Also, if I tick the mirror screen button, I can't select 1440x900 as my resolution, which means I'm stuck with crappy 1352x864.

---

### Post by Tamlynmac on 2008-11-05
I'm wondering if this is an issue with your video driver at the 1440x900 resolution. Since it functions at 1352x864.

Hopefully, someone else may have experienced this problem. You want to post your system especially video. 

Bump

---

### Post by Nevon on 2008-11-06
I solved it! I unticked the mirror screen-button, selected the "unknown" screen and set the resolution to none. Then I selected the '16" laptop' screen and set it to 1440x900. Then I just logged in and out, and voila! It worked!

---

### Post by Tamlynmac on 2008-11-06
I very happy you were able to resolve you issue. Seems often times with Ubuntu tenacity equates to success...

Good Luck

---

