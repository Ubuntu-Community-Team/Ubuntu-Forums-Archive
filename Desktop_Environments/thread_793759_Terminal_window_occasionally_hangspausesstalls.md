---
title: "Terminal window occasionally hangs/pauses/stalls"
date: 2008-05-14
forum: Desktop Environments
---

### Post by quinthar on 2008-05-14
Is anyone else experiencing a sporadic issue where the terminal becomes temporarily non-responsive?  The mouse continues working and the keyboard works fine with other applications during the hang.

(I'm not sure if the mouse/keyboard input works with other terminals during the hang, and I'm not sure I can mouse-select text within the hung terminal -- I'll check that next time) 

It always corrects itself after 5-10 seconds, but is really annoying regardless.  At first I thought it was a vim thing, but then I noticed it once while just tailing a logfile -- thus I think it's actually a terminal thing.  Here are some system stats if this helps nail it down:

- Ubuntu 8.04
- Full-disk encryption from the alternate install CD
- Gnome desktop
- Compiz with "Extra" visual effects
- Sony TZ270N laptop

Is there any other information I can provide that would be helpful?

Does this issue sound familiar to anyone else?

And is this even posted in the right forum?

Thanks!

-david

---

### Post by quinthar on 2008-05-23
Digging into this a bit more, I *think* it has something to do with the trackpad -- like perhaps I'm tapping it or something.  I haven't quite nailed it down.

---

### Post by sdennie on 2008-05-23
Have you explicitly done anything to put your disk into standby mode?  On battery I set mine to quickly go into standby and uncached disk reads stall for a few seconds as the disk spins back up.

---

