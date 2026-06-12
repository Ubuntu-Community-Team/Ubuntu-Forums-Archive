---
title: "Gnome integration in Compiz leading to improper behavior"
date: 2010-07-14
forum: Desktop Environments
---

### Post by warnec on 2010-07-14
Hi. I wonder if any of You experienced the same behavior - if You did, it seems like a good idea to file a bug.

When setting "Gconf Configuration Backend" in CCSM's Preferences and ticking the "Turn integration with desktop environment on" box, some of window shortcuts become impossible to change.

For example, I use Alt+Mouse2 to toggle window's menu and Alt+Mouse3 to resize a window (I set it that way in ccsm, and it worked).

But when I enabled desktop integration Mouse2 was used to resize, and Mouse3 to toggle window menu, like in Metacity. Even though it seemed possible to change these options in ccsm, the changes weren't applied (I wasn't able to set it the way I had it before).

And when I used ex. Ctrl as the modifier button for resize (Mouse2), Ctrl was also used for Mouse1(move window) and Mouse3(window menu) even though I only set one option!

This strange and erratic behavior seemed like a try to provide a consistency with Metacity shortcuts, but it was described nowhere in ccsm. 
Without the help on Compiz's IRC channel users, I wouldn't be able to find out what's causing the strange behavior.


That explained, it surely seems like a bug - the question is, where to report it? Does it seem like an Ubuntu or Compiz issue?

**PS (all the time I'm talking about that little tick in the Preferences menu, not the "Gnome Integration" plugin. I had that plugin enabled all the time as well, and it didn't cause any problems) **

---

### Post by warnec on 2010-07-20
So, noone else experienced this?

---

### Post by mcduck on 2010-07-20
Have you checked Gnome's keyboard shortcurt configurations? I would pretty much imagine that "Gnome integration" in Compiz would mean merging the shortcuts as well, and using Gnome's settings & dialogs when possible.

If that's the case then it of course isn't a bug, although CCSM could really explain some of the settings better (which would make it a feature request for CCSM).

---

### Post by warnec on 2010-07-23
How do I check it? I see I've got Alt as a modifier in System->Preferences->Windows , but have no idea how to check if Mouse2 is assigned to resize and Mouse3 to toggle window's menu.

---

