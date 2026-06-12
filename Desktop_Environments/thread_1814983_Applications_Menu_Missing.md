---
title: "Applications Menu Missing"
date: 2011-07-30
forum: Desktop Environments
---

### Post by Commander_Bob on 2011-07-30
I got sick of Unity's problems today so I decided to switch back to the classic desktop and the Applications menu is unpopulated. Only a small black box about 5px tall and 30px wide shows up with nothing in it.

Any ideas why I can't see any of my applications?

---

### Post by westie457 on 2011-07-30
Give this a try ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

It might work. No harm if it does not.

---

### Post by Commander_Bob on 2011-08-05
Nope, didn't do anything. I've tried rebooting and all that but nothing seems to work.

---

### Post by fdrake on 2011-08-05
> **Commander_Bob said:**
> Nope, didn't do anything. I've tried rebooting and all that but nothing seems to work.

right click on "Application tab" and select edit menu. check and uncheck your apps.

---

### Post by Commander_Bob on 2011-08-05
The window for editing the menus never opens.

---

### Post by wildmanne39 on 2011-08-05
Hi, did you do a clean install or upgrade?

What is the problem with unity?

---

### Post by Commander_Bob on 2011-08-05
It's a clean install but I've been using it for a while. I installed it around 11.04s release.

The Unity menu for me keeps refusing to close even when I have a full screen window. I think it has to do with Spotify but it's really annoying. I also hate how the tool bars in the windows go to the way top of the screen even if the window is not maximized. It's really annoying for programs like Gimp.

Also I don't like how it handles multiple instances of the same program. I like having a separate item for each.

---

### Post by mc4man on 2011-08-05
Try opening home folder and if need be view > show hidden files
open .config/menus and delete applications.menu

---

### Post by Commander_Bob on 2011-08-05
That did the trick! It works great now. Thank you!

---

