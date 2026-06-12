---
title: "time-admin causes UI freeze when changing settings"
date: 2006-08-13
forum: Desktop Environments
---

### Post by abaddon80 on 2006-08-13
This is now happening on two of my machines (a laptop and a desktop).  At first, I thought it was an issue isolated to my desktop, which was upgraded from Breezy to Dapper.  But, my laptop, which is a fresh install of Dapper, is also experiencing this problem now.

Symptoms: Mouse cursor is still responsive, in other words I can still see the mouse moving around the screen.  However, mouse clicks and keyboard input no longer registers.  Everything else still functions, I just can't interact via the UI.  I can ssh in from another box and kill the session (typically just restarting gdm), which then gets me back my keyboard and mouse.

I think I've narrowed it down to when I make a change to my time settings via time-admin.  For example, if I change the timezone or sync the clock, and then hit the "OK" button, the problem occurs.  If the time difference on the clock is less than a few seconds, synchronizing from time-admin has no problems.  However, if the time difference is rather large (like when changing time zones), this is when the problem arises.  

If I run ntpdate from the command line, as root, I have no problems, even when I've changed the timezone.

I've turned off my screensaver by unchecking the "Activate Screensaver when session is idle" in the Screensavers dialog.  I've also tried strace'ing the time-admin process, and while that exits normally, the interface still freezes.

Can anyone help shed some light on this issue?  Thanks.

---

