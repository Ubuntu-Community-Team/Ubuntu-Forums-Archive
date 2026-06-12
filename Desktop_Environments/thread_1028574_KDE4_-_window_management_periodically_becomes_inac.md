---
title: "KDE4 - window management periodically becomes inactive to mouse"
date: 2009-01-02
forum: Desktop Environments
---

### Post by reuben on 2009-01-02
Every so often kwin (or whatever KDE4 is using) becomes unresponsive to the mouse, meaning that I can't click on any of the windows to change focus. I can still alt-tab between them, but that's painful. Ideas on how to debug/fix?

---

### Post by hornet136 on 2009-01-22
I have the same problem.  I'm using kde4 under Kubuntu 8.10.

I've not been able to pin down any specific event but at times my system will stop responding to mouse clicks.  My USB keyboard works fine and I can tab to all my active windows.

My USB mouse still moves the cursor around the screen but the left/right or scrollwheel do not have any effect when used anywhere.  I've tried unplugging/plugging in the mouse with no effect.

I happen to be on a laptop and the built in touch pad also behaves the same.. I can move the cursor but no clicks or double taps etc.

I simply can restart X (no restart) and all is well for awhile.

I "thought" this might have to do with the 64 bit flash that I recently installed but I've not done any further investigation of that.

---

### Post by hornet136 on 2009-01-27
Looks like the problem is Xinerama related.. Here is a bug that seems to be the same issue we have.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

the first half is an older bug but the bottom half discusses our current issue.

---

