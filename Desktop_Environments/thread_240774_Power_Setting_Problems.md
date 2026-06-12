---
title: "Power Setting Problems"
date: 2006-08-21
forum: Desktop Environments
---

### Post by poet_will on 2006-08-21
Hey, everyone.  I have Ubuntu 6 on my Dell Inspiron 6000 laptop.  After ten minutes of being idle the screen goes black.  I changed the settings in Power Management Preferences to "Put display to sleep when computer is inactive for:" to Never.  I also changed the properties under Screensaver Preferences to "Set sessioin as idle after:" to 2 hours (the maximum).  However, I'm still getting my screen shut off after 10 minutes.  I have restarted after I changed settings and I'm still getting the problem.  Any suggestions?

Thanks

Will

---

### Post by wpshooter on 2006-08-21
Poet:

Believe it or not here is what I have found to be the key to this.

First make sure that you have the save changes to current session button marked.  Let me know if you do not know where this is located.

Try setting the screen saver function to 1 minute and then set the power management/screen blanking function to 2 or 3 minutes.

Then let the screen saver kick in and function after 1 minute activity and then after several more minutes the screen blanking function will go into effect.

After this move the mouse and bring the screen back on.  Then immediately restart the machine.

When the machine gets back to the desktop, then go into the screen saver section and turn the screen saver function off by unchecking the box.  Do NOT move the time slider.

Then wait several minutes and see if the monitor will go blank.  If and when it goes blank then bring it back on by moving the mouse.  Then restart the machine again.

When it comes back to the desktop this time, go into the screen blanking section and move the slider to NEVER.  Do not change anything in the screen saver section.

Then wait for 10 or more minutes and see if the screen stays on.

If it does you are good to go.  If not play around with this sequencing until you get it to work.  There is some strange problem in that the functioning of the screen saver and the screen blanking function are somehow interrelated.

Good luck.

---

### Post by yopnono on 2006-08-21
Use synaptic to check if you have more then one screensaver application.
If you did a dist-upgrade you may have the xscreensaver and gnome screensaver

---

### Post by poet_will on 2006-08-21
Yopnono - I unsintalled my screensavers and I'm still having the problems

wpshooter - I don't know where "save changes to current session" button is.  Could you point it out to me?


Thanks

Will

---

### Post by yopnono on 2006-08-21
Ok. did you have only 1 or more?. Make sure you install gnome-screensaver, and reboot and try again.

---

### Post by orb9220 on 2006-08-21
What wpshooter above is the process I used on my system. Had same problem. Had to do the process steps he outlined above. Don't ask me why it works it just did when nothing else did.

goto your system>prefs>sessions for save session on exit setting.

---

### Post by poet_will on 2006-08-21
yopnono - I believe I only had one.. so I re-installed the gnome-screensaver, rebooted... same problem.

---

### Post by wpshooter on 2006-08-22
> **poet_will said:**
> yopnono - I believe I only had one.. so I re-installed the gnome-screensaver, rebooted... same problem.

Follow instructions I gave in above post.

---

