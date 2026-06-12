---
title: "Recreating the ubuntustudio panel in ubuntu standard"
date: 2009-05-05
forum: Desktop Environments
---

### Post by shortridge11 on 2009-05-05
I installed ubuntustudio from a cd, and it came with all the packages, themese, and a specific panel set-up.  The panel i'm talking about is at the top of the screen where you launch everything.  I really liked how it was set up, but i can't remember how everything was oriented.  Can someone take a screenshot of the menu open?

Thanks

---

### Post by shortridge11 on 2009-05-06
A screenshot, or maybe a quick word on what layout they used?

---

### Post by joewski on 2009-05-07
> **shortridge11 said:**
> I installed ubuntustudio from a cd, and it came with all the packages, themese, and a specific panel set-up.  The panel i'm talking about is at the top of the screen where you launch everything.  I really liked how it was set up, but i can't remember how everything was oriented.  Can someone take a screenshot of the menu open?

Thanks
If you have installed ubuntustudio from cd simply create a new user. and log in to that new user. The new user will have the default settings of the ubuntustudio.

Since ubuntu studio is gnome based you can copy the gnome settings over from the new account to your existing account.

To do that log out of the new user back into your own account.

Next you need to backup the following home directory directories.
.gnome .gnome2 .gconf .gconfd .metacity (Just in case something stuffs up)

You may then use
$ rm -rf .gnome .gnome2 .gconf .gconfd .metacity

This deletes all your Gnome settings.
Now all you need to do is to log out and log in again.

Be warned that using this procedure looses your wireless key settings. You will need the key if your using a encrypted wireless connection.

---

### Post by shortridge11 on 2009-05-11
> **joewski said:**
> If you have installed ubuntustudio from cd simply create a new user. and log in to that new user. The new user will have the default settings of the ubuntustudio.


Well that's the thing- I don't have it installed from the cd, which is the problem.  I ran into compatibility issues with it running on my newer laptop, which has a terribly supported video card (Nvidia Geforce 9500M).  I installed the ubuntustudio theme, but i just need a screenshot of the bar so i can recreate it.

---

### Post by shortridge11 on 2009-05-13
or a short little word-list...basically i don't want to have to install it again. there's no live version of UStudio, or else i'd do that

---

