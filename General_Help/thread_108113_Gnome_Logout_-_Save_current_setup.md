---
title: "Gnome Logout - Save current setup"
date: 2005-12-25
forum: General Help
---

### Post by musther on 2005-12-25
I logged out of Gnome the other day and had Gaim and Skype open, I told it to save the current setup.  I thought this saved the current session so that when I logged back in, skype and gaim would be open and I could carry on, I'm sure that's what it used to do.  Anyway, I logged in, and indeed skype and gaim popped up, but they now do it every time I log in.  I know I can close them, and then save that setup upon logout, but is there a way to delete the saved setup, so that when I log in no programs load (I want to keep my desktop settings though, panels, background, scree saver, menu's etc).

Cheers

---

### Post by 23meg on 2005-12-25
You can delete the session in System / Preferences / Sessions / Session Options

---

### Post by redbull34th on 2006-06-09
I'm having a same/similar situation with Dapper after my from Breezy.

Post update-reboot, I had told Ubuntu to save my settings.  Now, I can't get rid of them.  I'm looking in my ~/.gnome folders, but can someone give me a hint of where this bugger is hiding?

Thanks!

---

### Post by musther on 2006-06-09
I managed to sort it out as per the post above, if you can't do it that way I'd post a new thread, this is a very old one and I don't think it'll get read much, I'm sure you'll get help if you post a new thread.  Well done for searching this thread out though!

Sorry I couldn't be of more help.

---

### Post by redbull34th on 2006-06-12
Thanks for your help.  Despite opening a new thread, no one else responded.

-----
I figured it out.  Gnome2 saves session settings in your profile:

/home/user/.gnome2/session

open session with gedit or vi or vim or pico or joe or whatever you want, and search for the offending program you wish to remove.

Save and exit, and restart gnome(logout or CTRL+ALT+Backspace).

Thanks!

---

