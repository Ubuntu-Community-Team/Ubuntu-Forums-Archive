---
title: "Preserve window positions after changing resolutions?"
date: 2012-09-16
forum: Desktop Environments
---

### Post by Stonecold1995 on 2012-09-16
I often have many windows open at once (I currently have 22 open and I sometimes have even more).  However, every time I do something that changes the screen resolution, the window positions seem to be forgotten.  For example, I often play the danmaku game Touhou Project through Wine, and the game has to re-size my screen to 800x600 (or something like that), which is totally fine.  When I quit the game, it changes the resolution back to 1920x1080.  However this has the annoying result of having all my windows scattered everywhere, and their sizes all changed.

If I'm right, this is what's happening:
- The windows are all in their normal positions
- The screen resolution lowers, forcing some of the windows to reorganize to fit the screen
- The screen resolution goes back to normal, but the windows have no "incentive" to move because their room isn't being restricted when the resolution grows.
- The result is that the windows are scattered all over the place

Is this correct?  If so, is there a way to get KDE to preserve the window sizes/positions?

---

### Post by bra|10n on 2012-09-16
The issue is caused by using the two screen resolutions. If you imagine this scenario from a co-ordinates perspective; eg, screen-center for one resolution will not be the same for the other resolution. So while you could set exact window positions on a per window or per application basis, there is no setting input unfortunately for @resolution_size.

You could investigate if setting up an 'Activity' for your game might be another option. This situation might be a valuable user-case scenario for the Activities developer to consider in the future.

---

### Post by Stonecold1995 on 2012-09-16
> **bra|10n said:**
> You could investigate if setting up an 'Activity' for your game might be another option. This situation might be a valuable user-case scenario for the Activities developer to consider in the future.

How would I set up an Activity specifically for my game?  Would that prevent the other virtual desktops from re-sizing when the game starts?

---

### Post by bra|10n on 2012-09-16
> **Stonecold1995 said:**
> How would I set up an Activity specifically for my game?  Would that prevent the other virtual desktops from re-sizing when the game starts?

I suggest you look [here]("http://forum.kde.org/viewtopic.php?f=67&t=93183") and perhaps repost your questions above there also. Providing some background to your situation, and what you'd like to achieve will also help.

---

