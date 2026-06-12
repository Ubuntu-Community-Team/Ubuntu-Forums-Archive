---
title: "Gnome-Panel startup error"
date: 2006-02-22
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-22
I hope that was a descriptive title kuz I won't be able to explain much better than that.  Every time I log into gnome with window maker as the window manager, I get repeating errors, like 10 times, saying "I detect another panel already running".  And after clicking "OK" 10 times, the panels are grey.  When you move them around, the menus and icons show up.  This only occurs on login.  Any ideas on how I go about diagnosing this and fixing it??

Thx for your time!

---

### Post by Xian on 2006-02-23
Could be several things.... Try opening a terminal in gnome and issuing a 'killall nautilus' command. Then logout/into gnome desktop. Any changes?? If you are saving your sessions then try a 'killall gnome-panel', save the session at logout, and login once more.

---

### Post by FIONEX on 2006-02-23
Hey, 
First of all, thx for the reply.  I tried doing killall gnome-panel and they shutdown but come right back up :S.  Then I tried logging out and saving the session, with no success.  I know for a fact that it's the gnome-panel because it's the same error message if I try # gnome-panel .  Where is the start up list?  There has to be one, right?

---

### Post by Xian on 2006-02-23
I understand that it is a gnome-panel issue but the most likely culprit is actually Nautilus. I would first try killing that app as mentioned previously, and then try not saving/saving your sessions before the next re-login. If you do have auto-save session enabled I would quickly do away with that as it is prone to cause many problems. If all else fails, just rename all your hidden gnome config directories in the home path and begin anew.

---

### Post by FIONEX on 2006-02-23
I managed to bring it down to the gnome config file called "session" where it has the restart commands in there and the RestartStyle hint.  Now it only produces one error rather than 10+.  I can deal with that, I just want to try and figure out why later on.  I'm still open to ideas.  Although I did try the nautilus thing.

---

