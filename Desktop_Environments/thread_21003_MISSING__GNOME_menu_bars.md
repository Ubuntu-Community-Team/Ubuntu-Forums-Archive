---
title: "MISSING : GNOME menu bars"
date: 2005-03-19
forum: Desktop Environments
---

### Post by SolarBear on 2005-03-19
That's mighty strange, I tell ya. I boot back into Ubuntu... and no bars. Those nice little bars on top and bottom of the screen are now gone. I see my desktop, a few icons and that is it.

Now, the 100,000$ question should be : what the HECK happened to your bars, SolarBear ? And my answer is : I have absolutely no idea. I didn't tinker with GNOME configs or anything, just installed and uninstalled a few things, nothing GNOME related, even.

Any ideas where my precious little bars went ?

---

### Post by Buffalo Soldier on 2005-03-19
Does restarting GNOME helps? (CTRL + ALT + BACKSPACE)

---

### Post by munki on 2005-03-21
And maybe restart gdm ?

---

### Post by rkn on 2005-03-21
Right-click on the background --> Open Terminal

In the terminal:

** $ killall gnome-panel **

gnome-panel was not cleaned up by Gnome the last time it was used.


Bob

---

