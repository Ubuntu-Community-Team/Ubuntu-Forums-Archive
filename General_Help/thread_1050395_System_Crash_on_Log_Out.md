---
title: "System Crash on Log Out"
date: 2009-01-25
forum: General Help
---

### Post by JoeIsom25 on 2009-01-25
I have been searching online for a solution (or even a confirmation that someone else has experienced this) and have come up empty handed.  I hope someone can point me in the right direction.

I have a fresh install of Ubuntu 8.10 on my Toshiba notebook.  The install went well, and everything seems to work very well, except when I try to log-off.  I can shut-down, and restart without any problems, but the log-off causes the system to "Crash" horribly.

When I log-off, I get a full screen memory dump and trace.  My Caps-Lock Light starts flashing, and I cannot recover at all.  I have tried all the tips I could find (ctrl+alt+backspace+backspace, etc...) and nothing can get me back running except holding the power button down. 

I think that I could debug this problem on my own if I could just capture this "trace" and memory dump some how.  There is so much stuff that is dumped to the screen that I get no useful information when the event occurs.  It all happens too fast.

I'm running the 32-bit version of ubuntu.  My system has an AMD 64-bit Dual-Core, with an on-board ATI 3100 video card.


Are there any resources I should read that describe this problem?  Is there a way to capture the data of a system crash (trace and dump) to a text file, so I can read through it when I reboot the system?

---

### Post by dcstar on 2009-01-25
> **JoeIsom25 said:**
> I have been searching online for a solution (or even a confirmation that someone else has experienced this) and have come up empty handed.  I hope someone can point me in the right direction.

I have a fresh install of Ubuntu 8.10 on my Toshiba notebook.  The install went well, and everything seems to work very well, except when I try to log-off.  I can shut-down, and restart without any problems, but the log-off causes the system to "Crash" horribly.

When I log-off, I get a full screen memory dump and trace.  My Caps-Lock Light starts flashing, and I cannot recover at all.  I have tried all the tips I could find (ctrl+alt+backspace+backspace, etc...) and nothing can get me back running except holding the power button down. 
.........

I'm running the 32-bit version of ubuntu.  My system has an AMD 64-bit Dual-Core, with an on-board ATI 3100 video card.
........?

I can't help with capturing info, but since logging off provides a new login screen it may be the problem is in the video drivers. I would suggest the following:

[LIST=1]
[*]Download and try the 64bit version of Ubuntu
[*]See if there are different video drivers available for you current version
[/LIST]

---

