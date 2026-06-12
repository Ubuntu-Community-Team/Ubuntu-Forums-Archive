---
title: "suspend without password"
date: 2009-04-13
forum: General Help
---

### Post by Pacopag on 2009-04-13
Hi.  Is there a way to set things up so that when I go to "suspend" mode I don't have to enter my password to get back in?  The problem is that when I try to enter my password, it doesn't work;  I type it in, but the little circles "i.e. hidden characters" where the password goes don't show up, and when I click "unlock" or press enter it says that I used the wrong password.  It's like the keyboard isn't working or something.  Fixing this problem would be nice, but it might be easier to just disable the whole password thing.

---

### Post by sdennie on 2009-04-13
You can disable the locked screen on resume if you want.  Hit Alt-F2 and type gconf-editor.  Navigate to /apps/gnome-power-manager/lock.  Uncheck suspend and hibernate.

---

### Post by Pacopag on 2009-04-13
Should "gnome_keyring_suspend" be checked?  Maybe that's my problem?

---

### Post by sdennie on 2009-04-13
From what it sounds like, you probably want nothing checked in the lock area.  Go ahead and uncheck everything.  It won't do any harm and you can always reverse it.

---

