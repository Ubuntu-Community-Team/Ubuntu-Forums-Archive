---
title: "Bizarre X/GDM/GNOME behaviour after crash"
date: 2009-03-19
forum: Desktop Environments
---

### Post by jamaisvu on 2009-03-19
Disclaimer 1: I'm running Jaunty, so I know it's all my fault.

Disclaimer 2: I've got a separate /home partition on the machine in question, so I'm not worried about data loss. I'm just curious if anyone has any ideas before I do a reinstall tonight.

Last night I had Firefox go beserk when trying to play an mpeg video. It suddenly started vertically scrolling all sorts of pretty colors all over my screen. I couldn't execute xkill and the three-finger salute didn't work, so I reisubbed it.

When it rebooted, as X (or maybe GDM, or maybe GNOME -- I had it set to log me in automatically (note to self: idiot)) started, I got the same behavior. I reached for the reisub again, and tried to mend X in recovery mode. Needless to say, it had no effect. I also tried mv-ing the .conf files in /etc/gdm in the hope it would generate some new ones, and that had the same result again.

I'm totally stumped by this, and I'm probably just going to do a reinstall anyway, but I'd be interested if anyone knows what's wrong.

---

