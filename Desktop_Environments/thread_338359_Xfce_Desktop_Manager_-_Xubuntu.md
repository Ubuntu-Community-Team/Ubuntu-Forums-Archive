---
title: "Xfce Desktop Manager - Xubuntu"
date: 2007-01-14
forum: Desktop Environments
---

### Post by Edowardo on 2007-01-14
I installed Xubuntu for the first time yesterday.  I have a few quirks to straighten out, but this one is driving me nuts.

Apparently Xfce desktop settings (manager) was taken over by gnome or nautilus, at least according to the boards. The right click on desktop feature is gone, as well the wallpaper. I can go under Applications >> Settings >> Desktop Settings, and check off the "allow Xfce to manage the desktop" but only for an instant will it work; restoring my desktop wallpaper until restart.

Things I've tried/checked:
Nautilus has taken over - - - -	It's not installed I believe, I use Thunar.
Gnome apps are running - - - - Running or not, problem continues.
Try different sessions - - - - Nope
Reinstall Xfce - - - - Attempted, but failed, need clearer instructions from what I found.
Sessions Startup - - - - Turned off launching Gnome, KDE and auto save session.

Any ideas?

---

### Post by john.nicholls on 2007-01-14
If the right-click menu and the wallpaper are gone, probably xfdesktop is not running. Use alt-f2 to open a window, and enter xfdesktop.

---

### Post by Edowardo on 2007-01-14
> **john.nicholls said:**
> If the right-click menu and the wallpaper are gone, probably xfdesktop is not running. Use alt-f2 to open a window, and enter xfdesktop.

Ah yes, scratch that idea too. Xfdesktop is definitely running. Regardless I did try your idea again. Still a no go. Xfdesktop is having a battle between another desktop manager. Which one is the question.

---

### Post by john.nicholls on 2007-01-15
> **Edowardo said:**
> Ah yes, scratch that idea too. Xfdesktop is definitely running. Regardless I did try your idea again. Still a no go. Xfdesktop is having a battle between another desktop manager. Which one is the question.

To see what else is running, open a terminal and type ps aux

---

### Post by Dwood108 on 2007-10-20
Try this:

   1. In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."
   2. Log out and log back in.
   3. Click 'New Session' when the session selector appears, and name it whatever you want.
   4. The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.

If this works you should be able to turn off the session selector at startup and login  directly to your new session.

---

