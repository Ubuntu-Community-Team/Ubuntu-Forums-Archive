---
title: "Mouse drags/Edge-flipping w/3 monitors"
date: 2008-10-28
forum: Desktop Environments
---

### Post by Paegus on 2008-10-28
I'm trying to get a triple-head setup to work properly but I'm running into some problems.

I Have 3 monitors: 2x 1280x1024 and 1x 1440x900. Physically they're arranged 1280x1024 (:0.1), 1440x900 (:0.0), 1280x1024 (:0.2). As far as the computer is concerned, I've tried having them both 1280x1024:0.1, 1440x900:0.0, 1280x1024:0.2 and 1280x1024:0.2, 1280x1024:0.1, 1440x900:0.0 (or the other way around) but each configuration leads to a similar set of problems.

1: The mouse doesn't wrap when there's not more than 1 workspaces. This is specifically annoying in the 1280x1024:0.2, 1280x1024:0.1. 1440x900:0.0 virtual layout.
2: I cannot drag windows from one X display to another be that 3 Separate or Twinview and 1 Separate: 2560x1024:0.1 & 1440x900:0.0
3: In separate X mode, each monitor has it's own set of workspaces and I can't find where to reduce them to 1 other than for the primary (display :0.0)
4: In Twinview mode the sizing becomes an issue with 1280x1024 and 1440x900 as they make poor bed-fellows. 1280x1024 and 1280x1024 however do make a nice wrap from far Left to far Right but then the mouse doesn't wrap back over to the side of the 1440x900 and similarly I STILL can't drag windows between the X displays (2 cards).

Other than using Xinerama which unfortunately disables xgl & still doesn't provide for a mouse wrap, is there any way of getting this to work smoothly?

I'm going to try firing up Synergy and have that wrap things for me but it doesn't let you carry over mouse drags...

Cheers in advance.

---

