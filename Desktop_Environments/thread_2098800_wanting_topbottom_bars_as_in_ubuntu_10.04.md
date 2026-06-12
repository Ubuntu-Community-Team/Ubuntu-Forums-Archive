---
title: "wanting top/bottom bars as in ubuntu 10.04"
date: 2012-12-27
forum: Desktop Environments
---

### Post by aspergerian on 2012-12-27
My Xubuntu machine is an Acer 1410 netbook, 64bit, 4g ram. Screen is 11.6 inches. Xubuntu 12.04 places unneeded icons on my desktop. 
Eg, [http://xubuntu.org/wp-content/uploads/2011/09/precise_01.png](http://xubuntu.org/wp-content/uploads/2011/09/precise_01.png)

1) Removing the horizontal icons was easy. I'd like also to remove the vertcal icons on left side. 

2) Furthermore, having oft-used applications and open programs on top-bar crowds both categories and makes them too small in top bar. Is there a way to set Xubuntu 12.04 so that the desktop looks and functions like the desktop in Ubuntu 10.04, with preferred applications in top-bar, with open programs in bottom bar? 
Eg, [http://en.wikipedia.org/wiki/File:Ubuntu_10.04_pre-alpha_screenshot.png](http://en.wikipedia.org/wiki/File:Ubuntu_10.04_pre-alpha_screenshot.png)

---

### Post by Merrattic on 2012-12-27
**Desktop Icons:**
To remove desktop icons, got to Settings > Desktop > Icons > Appearance and for Icon Type select none, and also untick all the boxes you can see.

**Panels:**
You need to edit your top and bottom panels and what you have on them. Settings > Panels (or right click on a panel and select Panel Preferences. Suggest you start off by unlocking panels, change the bottom panel to a vertical panel and always show, then drag the top panel to the bottom, then change the newly created side panel to horizontal and drag up to the top. Individual items and widgets can then be moved between your top and bottom panels as you wish. You should eventually get to a 10.04 look.

n.b. the widget that shows open applications is called "Window Buttons"

---

### Post by aspergerian on 2012-12-28
Merrattic,

Thank you for the prompt reply. I followed your instructions as far as I could (managed to remove unneeded icons from left side of desktop). However, I couldn't restore Xubuntu's horizontal panel of large icons along bottom of desktop, so going further has been impeded. 

You wrote, "Suggest you start off by unlocking panels, change the bottom panel to a vertical panel and always show, then drag the top panel to the bottom, then change the newly created side panel to horizontal and drag up to the top."

How do I restore currently hidden bottom panel so that it can be changed to a vertical panel?

---

### Post by Elfy on 2012-12-28
Right click a panel - panel preferences 

or 

settings - panel

Then you can change either - there's a dropdown to set which panel you are editing.

Unless you've deleted the bottom panel - in which case just create a new one and populate it with what you want.

---

### Post by aspergerian on 2012-12-28
Elfy,

Thank you. I found [http://ubuntuforums.org/showthread.php?t=2037039](http://ubuntuforums.org/showthread.php?t=2037039)

I'm now learning how to populate my newly created top panel & how to have bottom panel (formerly top panel) show only open programs. 

Progress is occurring.

---

### Post by aspergerian on 2012-12-30
The manipulations set forth in this thread have been helpful. Much used programs now have an icon in what has become top-horiz bar. Programs open appear in bottom-horiz bar. Overall, my newly arranged desktop works better for my eyes, given the 11.6 inch screen.

I have been unable to move wifi icon and user name from what is now bottom bar to what is now the top bar. Also, Xubuntu has a move-to-right arrow for items now in top-bar, but I haven't found a move-to-left arrow for items in top-bar. Perhaps there are solutions for these last items?

---

### Post by Elfy on 2012-12-31
You can't (afaik) move things from one bar to another, remove from one and add to the other.

Moving - the arrow is not of consequence - you can move things wherever you want them. Click move - and then drop it where you want.

---

### Post by Elfy on 2012-12-31
> **superDave972 said:**
> If you wanted the desktop environment on 12.04 like it was on 10.10, why not just take the easy way and install the Gnome DE by searching for it in Ubuntu Software Center? Then, you just have to log out, choose Gnome Classic, log back in, and you're all set.

Exactly what does Gnome desktop have to do with Xubuntu or this question?

Offtopic posts removed.

---

### Post by superDave972 on 2012-12-31
Just read the question wrong. That's all. Thought he had Ubuntu 12.04.

---

### Post by aspergerian on 2012-12-31
Elfy,

Thank you again. For what was originally Xubuntu's bottom bar and is now my computer's top bar, all icons are left justified. Is there a way to undo left-justified so that I can distribute my-new-top-bar icons without left-justification and without right-justification?

---

### Post by Elfy on 2012-12-31
You could try adding seperators.

Then you can expand them, either by right clicking on the seperator or editing it's properties in Settings - Panel.

It might be easier to do it in settings - you can play with moving it and expanding without the need to be right clicking.

You'll need to experiment to get it how you want it, I only have one panel, at the bottom in the right corner of the left hand monitor - so it's more or less central to both monitors.

---

### Post by aspergerian on 2012-12-31
I have achieved new top- and bottom-bars I can work with. Using separator helped. A screenshot is attached - with appreciation.

---

### Post by Elfy on 2012-12-31
Excellent, it's all good fun eventually :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229398&stc=1&d=1356979978[/IMG]

---

### Post by Merrattic on 2013-01-01
> **Elfy said:**
> You can't (afaik) move things from one bar to another, remove from one and add to the other.

Moving - the arrow is not of consequence - you can move things wherever you want them. Click move - and then drop it where you want.


^^^^^
It is possible to move the indicator plugins from one panel to another. Just right click in the right place and you will get a move option in the context menu.

Also aspergerian, I see you still have some icons on your desktop to the left ;)

You might also want to try out the Faenza Icon theme, all icons as little rounded corner equal sized squares....

---

