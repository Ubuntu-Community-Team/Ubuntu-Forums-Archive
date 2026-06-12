---
title: "in Xubuntu, desktop items disappeared, still accessible with file manager"
date: 2020-02-24
forum: Desktop Environments
---

### Post by kitandkaboodle on 2020-02-24
[COLOR=#000000][FONT=Verdana]I've been using xubuntu (xfce) 18.04 LTS (just updated) on an old Dell Optiplex 755 for more than a year. It's been working really well for me, actually.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]A couple months ago, just after loading some updates, all the items on my desktop disappeared. I can still access all the items via the Desktop folder via the File Manager in the "mouse menu", and I still see the background image, but I can't see any files on top of the background image, nor move any files or folders onto it. The screen desktop is just a pretty picture! 

I can't find any settings to try to reset the desktop.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Any ideas to fix this?[/FONT][/COLOR]

---

### Post by ajgreeny on 2020-02-24
Right click on the desktop and see what selections you have in the **Icons** tab of **Desktop Settings**.

Do you see the panel or has that disappeared as well?

---

### Post by him610 on 2020-02-24
> Dell Optiplex 755 I used one of those at work about 10 or so years ago. 
It could be that during the upgrade some previously configured Desktop Settings did not get carried through. I have also seen instances where somehow on the desktop presented, the normally seen icons and panel are outside the boundaries of the monitor, but they are there, just unseen. There should be a way to pull up a menu you can use to get to desktop settings.
What happens if you right click on the desktop?

---

### Post by kitandkaboodle on 2020-02-25
Hi ajgreeny and him610--right clicking desktop produces nothing.  "Settings" in the mouse menu does not include any "Desktop Settings" I've searched around in some obvious other places there, but haven't found any desktop-related ones other than ones that just seem to change the appearance design elements. That's why I posted.

---

### Post by ajgreeny on 2020-02-26
Use command ***xfdesktop-settings*** to open the desktop settings dialogue and see what that shows you.

It may also help to see what resolution your screen is set to use currently, from command ***xfce4-display-settings*** if you can't get to the display setting dialogue from the menu.  Too low a res setting could perhaps mean that the icons are off the viewable area, though that seems unlikely to me.

---

### Post by kitandkaboodle on 2020-02-26
Thanks for idea. I can access Display in Settings, but it was already set for the max res, 1280x1040. I toggled it to a lower res temporarily, applied, then back to original again, but no difference in problem.

---

### Post by him610 on 2020-02-27
> Use command xfdesktop-settings ...
On the tab icons page under Default Icons, you can see, or specify which icons will be displayed on your desktop
[ATTACH=CONFIG]285100[/ATTACH]

---

