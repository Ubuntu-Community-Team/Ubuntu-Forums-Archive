---
title: "Compiz- Problem"
date: 2011-05-05
forum: Desktop Environments
---

### Post by Antje on 2011-05-05
Hey.
I installed Compiz and tried some adjustments, and now my panel (and also the upper bar) is gone and I can't find a way to reopen Compiz (or any other program) to repair it.
What can I do?
Thanks in advance!

---

### Post by Copper Bezel on 2011-05-05
Unity is actually run by Compiz; what you installed was the Compiz configuration tool. Do you remember what setting you changed that caused it to crash?

Press Ctrl+Alt+T to open a terminal emulator.

If you remember what changes you made, run [font="Courier New"]ccsm[/font] and revert them, then run [font="Courier New"]unity --replace[/font], which will reactivate Compiz with the Unity UI enabled.

If you don't remember, follow [_this guide_](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html) to reset Unity and Compiz to their original settings. Just running [font="Courier New"]unity --reset[/font] and [font="Courier New"]unity --replace[/font] might solve it, or you might need to completely reset CompizConfig, with

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
unity --replace
```

---

### Post by Antje on 2011-05-05
Ok, I tried it, but now even the Ctrl+Alt+T -Combination does not work.

---

### Post by tekkidd on 2011-05-05
Log out then log back in selecting "Ubuntu Without Effect" as your desktop, then you should be able to fix the things from their

---

### Post by Copper Bezel on 2011-05-05
That's unfortunate. Do you have automatic login enabled, or do you see the login screen when you start the computer? If you don't have automatic login enabled, then you can at least restart and switch to Classic mode from the Session menu that appears below the login box after you select your username, then run the command to reset Compiz and Unity from there.

If you do have automatic login enabled, there's a trick to get back to the login screen, but this might be simpler:

* Try pressing Control+Alt+F1 to get to a console (you can get back to the desktop with Control+Alt+F7). 

* Log in and type and run the gconftool command above.

* For good measure, try running Unity --reset, too, although I think that one has to interact with the GUI and won't work here and should be redundant after resetting Compiz anyway.

* Restart, and Unity should be back to normal.

---

### Post by Antje on 2011-05-05
Ok, this worked pretty well, thanks for you help!

---

### Post by Copper Bezel on 2011-05-05
Excellent. = ) Please mark the thread as Solved in Thread Tools at the upper right.

---

### Post by nagromlt on 2011-07-29
> **Antje said:**
> Hey.
I installed Compiz and tried some adjustments, and now my panel (and also the upper bar) is gone and I can't find a way to reopen Compiz (or any other program) to repair it.
What can I do?
Thanks in advance!


Same problem, and unable to get into the panels or terminal (hot commands seem disabled).  I'm sure rebooting would fix, but I really wanna do this w/o having to resort to that.
Tried other threads related to this and same advice but not able to comply.

---

