---
title: "Suspend on a Dell workstation?"
date: 2010-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by feffer on 2010-09-03
Just got a Dell XPS9100 workstation, with Win7, and installed Ubuntu 10.04 as dual boot. Everything works so far except Sleep mode -- suspend. 

On the Win7 side the machine suspends normally. The hdd spins down, monitor goes to standby, and the machine start button blinks. The fan is either off or going so slowly I can't tell.

When I try to sleep in Ubuntu, the monitor goes down, and it seem like it's trying to go into suspend-to-ram mode, but then the login box pops up on the monitor, and it never goes further. The pm-suspend.log in /var/log/ seems to confirm this (I can post that if needed). I've been searching for a way to get suspend working on this workstation, but most info is about laptops, not workstations, or the info is a few years old. I know a lot of work has been done on power management in Debian recently, and I don't want to use out-dated methods that may mess things up worse. 

I've tried various settings under Power Management, but no success yet. Might I need to install some additional app like "hibernate"? Any help would be appreciated.

thx,
feffer

---

