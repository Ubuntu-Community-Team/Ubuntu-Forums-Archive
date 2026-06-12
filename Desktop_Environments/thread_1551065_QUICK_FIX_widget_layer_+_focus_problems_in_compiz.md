---
title: "QUICK FIX: widget layer + focus problems in compiz"
date: 2010-08-11
forum: Desktop Environments
---

### Post by Zorgoth on 2010-08-11
I used to have problems where using the widget layer would cause me to lose keyboard focus on my working application, or sometimes even make it so I couldn't click to focus.  I noticed there are a number of unanswered threads on this subject,

I struggled with this for a couple hours and found a fix that works for me:

In the Window Rules plugin in ccsm, add all of the widgets to "No Focus".

This works for me.  For some reason it didn't work on the ccsm window I changed it in until I restarted ccsm, which is weird, but I have not had any widget/focus problems since!  I hope this helps someone!

---

### Post by Zorgoth on 2010-08-11
False alarm - after another 15 minutes of experimentation, I found that this did not work perfectly.  The widgets will not take keyboard focus from the current window, but to pass keyboard focus to another window you need to turn them off.

---

