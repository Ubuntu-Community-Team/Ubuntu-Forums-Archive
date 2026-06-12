---
title: "Unity Issue After Switching GPU PCIe Slot"
date: 2013-06-06
forum: Desktop Environments
---

### Post by Kodeine on 2013-06-06
I had no quarrels with my radeon 7790 in the previous PCIe slot. However the other available slot has more bandwidth and so today I decided to switch. Initially both unity and the window borders wouldn't load. After reinstalling the latest stable binary blob driver, the window borders now do appear. However unity still does not. Here is unitys output [http://pastebin.com/S6qvRzNP](http://pastebin.com/S6qvRzNP)

After running unity the window borders no longer appear.

**I try lots of different suggestions from Google and then just as I decide it's time to make a post on the forums I then immediately find the current solution, tsk.
I got unity back via the two following unity commands

dconf reset -f /org/compiz/
setsid unity

---

