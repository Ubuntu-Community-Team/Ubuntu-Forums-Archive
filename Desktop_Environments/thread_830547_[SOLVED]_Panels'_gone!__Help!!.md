---
title: "[SOLVED] Panels' gone!  Help!!"
date: 2008-06-15
forum: Desktop Environments
---

### Post by lieuhon on 2008-06-15
I am using xubuntu.  The penals, top and bottom, have gone after a crash, therefore I can only use command to open application and and even shutdown the system.  I don't know how to get the panels back.

This happened after I tried to empty the trash bin and the system return a message that told me it can't connect to the trash bin.  Then I got a the window froze and a "No Entry" sign replaced the trash bin icon at the right-bottom conrer.

I did a restart after that and then all the panels have gone.

---

### Post by powerpleb on 2008-06-15
hit ALT + F2 and type in 'xfce4-panel'

if this does not work hit ALT + F2 and type in 'xfce-setting-show'
Choose the panel icon and use the Panel Manager to add panels (the little '+' icon adds panels)

---

### Post by lieuhon on 2008-06-15
Thanks for that.  I will do this when I get back.  Many thanks

---

### Post by jw5801 on 2008-06-15
You can also right click on the desktop (gives you your normal applications menu), and open "Settings > Settings Manager" then open the panel dialog to add the panels back again. Presumably if the panels are no longer there, it is because their configuration files went missing or became corrupt, simply restarting xfce4-panel therefore will not restore them.

---

### Post by valourama on 2008-06-16
> **powerpleb said:**
> hit ALT + F2 and type in 'xfce4-panel'

if this does not work hit ALT + F2 and type in 'xfce-setting-show'
Choose the panel icon and use the Panel Manager to add panels (the little '+' icon adds panels)

I tried the commands above, but the as per the previous post before mine, the commands are not responding.  Guess my files are corrupted.  I wonder how I can restore them without reinstalling... sigh...

---

### Post by Yuki_Nagato on 2008-06-16
Can you go to the Synaptic package manager and search for the xfce desktop environment?  Mark the xfce desktop environment for reinstallation, and then apply it.  Perhaps you can merely reinstall the GUI, and not all of Ubuntu.

---

### Post by VMC on 2008-06-16
> **valourama said:**
> I tried the commands above, but the as per the previous post before mine, the commands are not responding.  Guess my files are corrupted.  I wonder how I can restore them without reinstalling... sigh...

Have you tried this:

```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup

```
Then logout and back in again.

---

### Post by jw5801 on 2008-06-16
> **VMC said:**
> Have you tried this:

```
mv ~/.config/xfce4/panel ~/.config/xfce4/panel.backup

```
Then logout and back in again.

Not a bad call. You can run "xfce4-terminal" in the run prompt to get a terminal. Also, try running the same commands mentioned earlier in a terminal and see what is output, might provide some debugging insight.
```
xfce4-panel -r
xfce-setting-show
```

---

### Post by lieuhon on 2008-06-16
I run the command 'xfce4-panel' and this fixed the problem.
Many Thanks

---

### Post by whoscheesemine on 2008-11-30
entering that command only makes it work for the current session, to permanently fix this you need to run your updates

---

