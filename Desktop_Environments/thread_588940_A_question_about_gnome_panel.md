---
title: "A question about gnome panel"
date: 2007-10-23
forum: Desktop Environments
---

### Post by waldorsockbat on 2007-10-23
I want to delete all panels in Gnome but according to info I have found I must have 1 panel.My question is, is there a way to delete BOTH panels or if not is there a way to make the top panel completely hide?I have pixels set to the minimum allowed. I have  conky,cairo (forgot to add to sessions so it's not in the screenshot)clock, awn with the  quit,application,stacks applets running. I do not need the panels and I want delete them  to make my desktop nice and clean but the top panel will not completely hide or delete.

Here is a screen shot to show you what I am talking about,notice that half the top panel is still visible when I have auto hide enabled

---

### Post by aysiu on 2007-10-23
Go to System > Preferences > Sessions > Current Session

Click on *gnome-panel*. Under *Style*, select *Normal* instead of *Restart*.

Then, click *Remove* and *Close*

Finally, press Alt-F2 and type ```
killall gnome-panel
``` I think your panel should be gone.

---

### Post by waldorsockbat on 2007-10-23
OK it worked kinda. When I go to session and remove gnome panel the panel disappears but alt+F2 no longer works,If done in reverse order the panel disappears until I log out/log in and then it's back.

---

### Post by Alucard-sama on 2007-10-24
Why Not Just Install A Different DE or simply use a WM that comes with some of the functionality of a DE (eg OpenBox)?

---

### Post by waldorsockbat on 2007-10-24
Well after starting up computer today it hangs on login..Just before login window I get a white screen and a busy curser and that it.I can boot into recovery mode but it uses Xfce because of mythtv install.So I need a command to run from terminal in recovery mode to restore the panel I deleted in Gnome, if that is even possible?

---

### Post by waldorsockbat on 2007-10-25
I hate to bump my own thread but I need help.

---

### Post by waldorsockbat on 2007-10-25
I have fixed it but I am not sure how.I booted into recovery and removed xfce through synaptic. booted restarted and I now have my gnome desktop back and the top bar is back as it was.I will hold off marking this solved until some one posts a explanation of how that fixed it.

---

