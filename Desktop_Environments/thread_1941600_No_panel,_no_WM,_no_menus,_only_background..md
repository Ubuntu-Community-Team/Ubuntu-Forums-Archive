---
title: "No panel, no WM, no menus, only background."
date: 2012-03-15
forum: Desktop Environments
---

### Post by linas on 2012-03-15
I rebooted today, first time in 3-4 months, and was greeted by a non-functional desktop. After logging in, my old desktop background showed, but nothing else: no panel, no menus, nothing.  Killed X, logged back in, this time selecting one of GNOME, Unity or Gnome Classic from the greeter menu; all three behaved exactly the same way.

Selecting the "rescue session" from the greeter, I do get one small, lonely xterm. From that xterm, I am able to start metacity by hand, and start gnome-panel by hand, and after that, everything works. (well, almost everything... sadly, it failed to remember what windows I had open ...)

So, for the next 3-12 months (... till the next electrical power outage ...?), I'm good to go.  But this is incredibly annoying... Any clue where to even start debugging this?

This is 64-bit oneiric BTW on an old amd64 system.  I'm not even sure what other config info to report here: a proprietary nvidia graphics card; dual-screen setup ...

-----
After some experimenting; the compiz window manager is probably at fault; killing metacity and starting compiz causes all windows to become unresponsive to mouse clicks or keyboard typing.  Unable to focus on any window. desktop background becomes white. Killing compiz, restarting metacity puts everything back to normal.
-----
gnome-appearance-properties no longer exists, which means I cannot control metacity any longer! Arghh!  After gobs of googling I found this: [http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse](http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse)  
-----
<rant>About 5-7 years ago, Ubuntu "just plain worked"; now, you have to be a rocket scientist just to keep it running.  The above is only the 6th or 8th hack of the day; this morning, it wouldn't boot at all (lvm issues) then X11 wouldn't come up (nvidia issues), then the desktop... why is everything so broken, all the time?  I can only hope that Canonical finds its way again, as it seems to get a little more dazed & confused every year.</rant>

---

