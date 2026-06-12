---
title: "How can I edit the appearance of the Window Switcher?"
date: 2015-05-29
forum: Desktop Environments
---

### Post by chrisasl92 on 2015-05-29
Hello,

I am using Unity DE, and I would like to try editing the appearance of the window switcher (ALT + TAB).
In any theme I am using, should I edit CSS files? If so, which CSS classes are for the window switcher element? 
If editing CSS files of the current theme, then how can I proceed editing it? 
[B]
Some edit examples are: [/B]changing the background color, the border-radius, the edge around it.


System: Ubuntu 14.04.2

---

### Post by deadflowr on 2015-05-29
Limitly(?) you can tweak the border by editing/playing with the image files for Switcher in /usr/share/unity/icons.
Note you might want to keep a save in your home folder, because any update later to unity will overwrite your work.
(keeping a copy of your changes somewhere in your home will allow you to easily copy thoise changes back, if need be.)

Also, if you use gimp to adjust the images, you might need to reset the image mode to rgb, otherwise it might not show correctly in gimp.

Outside of that though, I would think you'd need to adjust these things from a source build of unity...
Since the default image for the switcher inherits whatever the settings for the launcher,dash,panel are.

My 2 cents.

---

