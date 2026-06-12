---
title: "change menu icon size"
date: 2010-05-14
forum: Desktop Environments
---

### Post by mtbeedee on 2010-05-14
I just upgraded from Hardy to Lucid and for some reason the only height the menu will use is 32 px.  I used to have it at 24 px before the upgrade and I want to make it that again.  How can I change the height of this icon/menu?

---

### Post by drs305 on 2010-05-14
Would you confirm you have tried right clicking the panel, selecting Properties, and tried adjusting the 'Size' in the General tab?

---

### Post by mtbeedee on 2010-05-14
Yes, that is set to 24.

When I unlock and move the menu itself off of that panel, the panel shrinks to the correct size.

I think this is icon theme related... I am using the Tangerine theme.

---

### Post by prshah on 2010-05-14
> **mtbeedee said:**
> How can I change the height of this icon/menu?

You have probably set a custom icon with size 32x32 instead of scalable. You can check by:

Press Alt+F2, and give the command ```
gconf-editor
``` In the window that opens up, navigate to "/apps/panel/objects/object_0" (the final path may be different; look for an entry "Tool Tip - Main Menu" in the right side pane to find the correct object).

In the right side pane, you can UNCHECK "use_custom_icon" and/or change the value of the "custom_icon" path to include a scalable image (usually from /usr/share/pixmaps/)

You will have to restart your gnome panels to see the change. The simplest way is to simply log out and back in, but if you are feeling adventurous, press Alt+F2 and give the command```
sudo killall -9 gnome-panel
``` (Note that the second method MAY screw up the placement of icons/applets when the panels reappear).

Please post back if you need more help.

---

### Post by mtbeedee on 2010-05-14
There are no objects under objects that have that "tool tip" thing but there is one that is menu_bar_screen0 on the left.

It has use_custom_icon unchecked.  I just checked it and added a custom_icon to some svg file.  Didn't fix the problem.  I changed the icon theme though and that fixed it.

---

