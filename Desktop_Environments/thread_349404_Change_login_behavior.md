---
title: "Change login behavior"
date: 2007-01-30
forum: Desktop Environments
---

### Post by an.echte.trilingue on 2007-01-30
Hey all.

I would like to change the login behavior in 6.06, if it is possible.

Namely, I would like change these things (in order of importance):
1.  Currently, when I go to logout-->switch user, and GDM opens up again, it will only sit there for a couple minutes before it drops back to the user.  I would like to change this so that it stays at the welcome screen indefinitely.
2.  Currently, when on the GDM welcome screen, if user A is already logged in and I select user A again, I get a dialogue box that asks if I want to go back to the old session or start a new one.  I would like it to just go to the old session automatically. 
3.  Currently, when I log in as user A, and then somebody else logs in as user B, and then logs out again, the screen goes straight back to user A.  Can I configure this so that it goes to the GDM welcome screen?
4.  I would like to configure gdm so that when I log in, the gdm welcome screen stays open on TTY7 so that I can always switch back to it with CTRL+ALT+F7 or something like that.

If anybody knows how to make these changes or where I can read about doing things like this, please let me know.

Thank you for you time

-mat

---

### Post by makara.aktee.sok on 2007-01-31
hey! 

try playing with 

/etc/X11/gdm/gdm.conf

don't forget to make a backup! 

I saw something interesting in it. 
# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

---

