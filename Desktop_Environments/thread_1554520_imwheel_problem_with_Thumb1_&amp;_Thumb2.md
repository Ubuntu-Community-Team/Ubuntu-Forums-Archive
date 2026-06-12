---
title: "imwheel problem with Thumb1 &amp; Thumb2"
date: 2010-08-16
forum: Desktop Environments
---

### Post by UncleBoarder on 2010-08-16
I'm new to Ubuntu so please tell me if I've made a mistake... I've spent the last two weeks searching/reading/troubleshooting, trying to get my multi-button trackball configured.  It works, but I want to change the buttons around and use one for a carriage return.

I've used xmodmap for remapping the buttons.  And imwheel for assigning the <CR>.  Both work, but not together.  I've narrowed it down to the fact that imwheel assigns both Thumb1 and Thumb2, but I have it configured to only assign Thumb2.  Which effectively erases my xmodmap for Thumb1.

My imwheelrc config has one line in it...

None,     Thumb2,     Return

Yet for some reason after running imwheel, I use xev and see that clicking Thumb1 (button8 ) it seems to be looking for a keyboard input.

Thumb2 gives me this (and it works)[INDENT] LeaveNotify event...
KeyPress event...
KeyRelease event...
EnterNotify event...

[/INDENT]But Thmb1 gives me this (and it does nothing... I did not define anything for Thumb1)[INDENT] LeaveNotify event...
EnterNotify event...
[/INDENT]No KeyPress event and no ButtonPress either.  Prior to running imwheel xev shows Thumb1 as button8.

I tried rerunning xmodmap after imwheel but that doesn't work either.  So my questions...

1) How do I stop imwheel from modifying Thumb1?

2) Or is there some way to use imwheel to just redefine Thumb1 as button8 which by default is BACK.

---

### Post by UncleBoarder on 2010-09-19
I believe the assignment of THUMB1 is a bug.

My solution was to assign THUMB1 as well and move on.  This issue is not resolved but I have a workaround.

If that means I should close this please send me an email.  Otherwise I'm leaving this open in hopes that someone has a better response.

---

