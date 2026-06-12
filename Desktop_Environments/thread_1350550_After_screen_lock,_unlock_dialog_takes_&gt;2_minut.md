---
title: "After screen lock, unlock dialog takes &gt;2 minutes to appear"
date: 2009-12-09
forum: Desktop Environments
---

### Post by MgFrobozz on 2009-12-09
This problem started after the last time update-manager suggested an update and I ran it. Among other things, it installed the 2.6.31-16 kernel (I don't think the kernel is involved in the problem, and I'm citing the number only to identify the update).

The system works properly if I lock the screen, and then attempt to unlock within a few minutes of locking. However, if I lock the screen, then leave it overnight, when I attempt to unlock in the morning the only thing visible on screen is the mouse cursor. The mouse cursor moves correctly, so the system is not locked up. About 3-5 minutes after I've started moving the mouse cursor, the unlock dialog appears, and then I can unlock the system. I've verified that cycling the power on the monitor does not fix the issue (this works on another workstation running ubuntu that has occasional shown an issue which is similar, but in which nothing is shown on-screen).

Any ideas about how to trouble-shoot this? I'm using gdm, and locking using the "Lock Screen" entry in the menu with an on/off button as the menu icon, and my user-name as the menu title. What app does that run, and does it have the ability to log debugging information that I can look at after an unlock?

---

