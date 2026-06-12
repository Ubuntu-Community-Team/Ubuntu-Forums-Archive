---
title: "Old logout dialog"
date: 2009-06-08
forum: Desktop Environments
---

### Post by unkilbeeg on 2009-06-08
It looks like the dialog box for logging out has changed in both Intrepid and Jaunty.  Instead of a full set of options (shutdown, reboot, logout, etc.) the only options presented are "logout" and "switch user."  

Is there any way to get the old behavior back?  That was a useful design.  

I'd really like to eliminate the "switch user" option altogether, but I could live with it if it were just one option among many.

---

### Post by NilsE on 2009-06-08
All of the options for logout, shutdown etc. are in the add to panel applet.  See if you can find the one you like there.

---

### Post by unkilbeeg on 2009-06-08
As separate icons.

In Hardy (and before) the logout dialog got you all of those in one swell foop.  That was convenient.

The current dialog is not so convenient, and it offers an option I really wish my users would never see, which is the "switch users" option.  So did the old one, actually, but it was at least somewhat hidden in the plurality of other options.

---

### Post by unkilbeeg on 2009-06-09
Am I the only one who would prefer the older, all-encompassing logout dialog?

---

### Post by NilsE on 2009-06-09
I personally liked the real old version where you were presented with the 5 or so icons when you clicked on the  icon on the panel.

I don't mind the new version that has all of them on the popup menu.  I am assuming you do not have the "Fast User Switch Applet" on the panel or you would see more options.

I think what you are looking for may be this

Right-click on the menu bar and "add to panel" and select shutdown

---

### Post by Roti78 on 2009-06-10
> **unkilbeeg said:**
> Am I the only one who would prefer the older, all-encompassing logout dialog?

My wife really hates the new logout panels :)
She would prefer the old one too!

---

### Post by unkilbeeg on 2009-06-10
> **NilsE said:**
> I personally liked the real old version where you were presented with the 5 or so icons when you clicked on the  icon on the panel.
I don't know that I'd call that "real old".  :)  All my production machines run Hardy, and that's what we have there.  And that's what I'm looking for.  One panel to rule them all.

> **NilsE said:**
> I don't mind the new version that has all of them on the popup menu.  I am assuming you do not have the "Fast User Switch Applet" on the panel or you would see more options.

I think what you are looking for may be this

Right-click on the menu bar and "add to panel" and select shutdown

I've done that on my test machine.  Still doesn't do it.  "Shutdown" gives you an option to shutdown, reboot, hibernate and suspend.  "Logout" gives you the option to log out or switch users.  I want *one* button that allows you to log out, shutdown or reboot.  I can live with hibernate or suspend, but I have no use for them.  I'd really rather have "switch users" go completely away, but I since that's included under Hardy, I suppose I could live with that too.

I really don't want two separate buttons, though.

---

### Post by floborg on 2009-06-12
Not only has one dialog been broken into two, but the new one does not play nicely with 3rd party gnome icon themes.  The Suspend icon can be fixed by linking to a suspend icon and renaming it "Sleep," but not the others (restart, hibernate).  I saw a bug report on it where the author kindly pointed out the exact lines of code that contained errors, but, as usual, the devs just try to justify the broken design and back-burner any work on it.

---

