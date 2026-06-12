---
title: "gnome main toolbar unexpected hide"
date: 2008-01-07
forum: Desktop Environments
---

### Post by elizh on 2008-01-07
Sometimes when I mouse over the gnome main toolbar, it unexpectedly disappears. My configuration is as shipped by System76, with hide arrows turned off and the 'human' theme. It's a Feisty installation on a tower with a wide screen. Generally this happens when I'm trying to mouse over and select something from the applications menu, but I don't get to the point of left clicking on my application because the toolbar disappears completely. 

Could I somehow be triggering a hide off the top of the screen, where the thin bit that should remain is logically off the top of the screen too? 

Is there any way for me to recover, short of a hard boot? 

(as a longtime unix user I would have expected 1) a key combo to restart the window manager 2) a key combo to log me out and get a new session 3) a key combo to soft boot. But in fact there are problems with all of these. Will be happy to start a separate forum thread for each, if needed. Basically if you don't have a main toolbar, there is no way to get a shell...)  

Regards, 

Elizabeth

---

### Post by balaknair on 2008-01-07
I'm a noob, not much experience, but I think instead of hard booting for something like this, you could just restart X11  by hitting Ctrl+Alt+Backspace, it'll also take you back to the log-in screen
I'm sure there are better steps, but this for me has been sort of the equivalent of Ctrl-Alt-Del in Windows. So till you do find the better steps, maybe this will be useful.

---

### Post by elizh on 2008-01-07
Thanks! this seems to work for a normal, healthy session, so hopefully it will work when the toolbar hides.

Still would like to know why it hides, and how to get it back again without restarting the session.

E

---

### Post by Casual Fan on 2008-01-07
> **elizh said:**
> (as a longtime unix user I would have expected 1) a key combo to restart the window manager 2) a key combo to log me out and get a new session 3) a key combo to soft boot. But in fact there are problems with all of these. Will be happy to start a separate forum thread for each, if needed. Basically if you don't have a main toolbar, there is no way to get a shell...)  

Regards, 

Elizabeth

You can use CTRL+ALT+a function key to switch tty's. You can press CTRL+ALT+SYSRQ+reisub to do a warm reboot. And you can press ALT+F2 and run "gnome-terminal" to get a shell.

---

### Post by elizh on 2008-01-09
All those key combos do seem to work, in a healthy session.
I haven't been able to test them when the toolbar hides, as the bug hasn't reoccured yet.

Further notes: When the toolbar vanishes, it just vanishes. It does not slide away in a direction, as with the left and right hide buttons. Is there a way to get it back without losing my session?

---

