---
title: "[SOLVED] Where did the top bar go?"
date: 2008-06-28
forum: Desktop Environments
---

### Post by I Use Dial on 2008-06-28
I was trying to accomplish two things and on reboot the top bar with commands and status and everything is now gone.

I was trying to add folder sharing (which was actually giving me an error) and XDMCP remote login.

Any ideas?  It wouldn't kill me to reinstall Gnome since I haven't done all that much it (fresh install).

---

### Post by bubba_169 on 2008-06-28
Press Alt+F2, in the dialog type 'gnome-panel' :D

---

### Post by I Use Dial on 2008-06-28
Nada - didn't do anything.

---

### Post by bubba_169 on 2008-06-28
Do you mean the command did nothing or the dialog didn't show at all?

---

### Post by I Use Dial on 2008-06-28
The command did nothing.  The Run Application dialog box came up, recognized the app, but running the app did nothing.

---

### Post by I Use Dial on 2008-06-28
I just ran Terminal and did sudo gnome-panel, and that got the panel up.  I have set up the computer to auto login, but that function had been working fine.  How do I fix this?

---

### Post by bubba_169 on 2008-06-28
Sorry if I dont quite understand what your asking ... you mean you want the gnome-panel to show after each login? When you have your panel open, and set up your desktop exactly how you want to see it after login, got to System->Preferences->sessions and in the session options tab click remember running apps

---

### Post by I Use Dial on 2008-06-28
Alright, so it's fixed.  After adding a new panel on the top I did a reboot and the old panel was back this time, so I deleted the new panel, rebooted, and the old panel was still there.  Strange.

---

### Post by rp3 on 2008-06-28
> **I Use Dial said:**
> Alright, so it's fixed.  After adding a new panel on the top I did a reboot and the old panel was back this time, so I deleted the new panel, rebooted, and the old panel was still there.  Strange.

I just had a similar problem, my panel was gone as well, but ALT-F2 didn't bring up the run command, so I restarted X (Ctrl-ALt-BackSpace) and started in Failsafe mode, the panels came back.  So I then set things the way I wanted and saved the session.

I restarted (reboot) and tried normal Gnome, and no panels?  Where is the file that the sessions info is saved?  Maybe I need to clean that out and try again?

:confused:

---

### Post by rp3 on 2008-06-28
> **rp3 said:**
> I just had a similar problem, my panel was gone as well, but ALT-F2 didn't bring up the run command, so I restarted X (Ctrl-ALt-BackSpace) and started in Failsafe mode, the panels came back.  So I then set things the way I wanted and saved the session.

I restarted (reboot) and tried normal Gnome, and no panels?  Where is the file that the sessions info is saved?  Maybe I need to clean that out and try again?

:confused:

I kept messing with it and now it's back when I run full GNOME?  Something happened with the graphics to where desktops effects went away, a reboot later, and turned back on it is now working as expected???

Oh wellll

---

