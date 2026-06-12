---
title: "System Freezes While Moving Windows Around"
date: 2011-11-11
forum: Desktop Environments
---

### Post by BarcSsarc on 2011-11-11
Hey guys,
  I'm planning to do a complete reinstall, to deal with a number of issues related to flaky Unity and Gnome-Shell, but thought to run this one by you first, to see if anyone had any ideas.

Basically, on occasion / frequently, my Unity/Ubuntu shell gets in this 'mood' where, when I move windows around, the system stalls completely.  It only happens while the mouse button is held down and the mouse is moving.  When I stop moving the window, everything 'catches back up.'  For all intents and purposes, everything else Unity-related / compiz-related is running beautifully, and quickly.  No apparent problems.
I tried disabling "Move Window" in the Compiz Settings Manager but, when I re-enabled it, my whole shell crashed, leaving all windows without any borders - and without any way to log out or start a terminal session.
After restarting, I opened a System Monitor session and watched the CPU graphs.  While idle, my four CPUs are running at about 4%.  While I'm moving a window around, the graphs are all frozen along with everything else, but, when the system 'catches back up,' I can see big spikes in all four CPUs from when I was moving the window around - CPUs 1&2 seem to be jumping to about 60%, CPU 3 is jumping to about 40% and CPU 4 is jumping to about 25%, when I'm moving a window around and the computer is stalled.

Anyone have any ideas?  I've tried resetting Unity and replacing the shell session, but neither of those works.

Thanks much for your time,
--BarcSsarc

Edit: I am running Ubuntu 11.10 on a Desktop PC, Nvidia GeForce 260, 8GB RAM.  Can't edit my personal settings, for some reason.  :/

---

### Post by tliketea on 2012-02-05
Hiho!

Same strange behavior here on an i3 sandy, 4gb ram ... laptop :-/

Screenshot attached -- no programs started except htop in a terminal and settings-manager.

Idea anyone? :)

Soon,
T

---

### Post by Last_Ship on 2012-07-15
I'm having the exact same problem. System completely freezes when I try to move a window. 4GB ram, Pentium 4HT. Any insight would be greatly appreciated.

---

### Post by tliketea on 2012-08-03
I think for me unchecking the option "Sync to VBlank" in CompizConfig Settings Manager did the work ...

Cheers!

---

