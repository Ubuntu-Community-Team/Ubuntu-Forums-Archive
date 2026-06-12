---
title: "Saved a session, now logging in takes forever!"
date: 2007-08-31
forum: Desktop Environments
---

### Post by thegibbling on 2007-08-31
I was trying to get conky to load at startup but it wasn't behaving properly so I decided to just save my current session and thought I would be fine.  Now it takes at least 7 minutes for Ubuntu to load up that session after login.  Is there a way I can get myself back to instant login? I don't want to blowout a working install which has suspend/hibernate semi working.

Thanks in advanced.

---

### Post by ajgreeny on 2007-08-31
Just start up the gnome-control-center and go to sessions.  There you can sort out exactly what you want to do in future.  Probably easiest and, I think, best to start afresh each time except for those things in the startup tab. This means setting things to not remember the last session.

---

### Post by thegibbling on 2007-08-31
But is there a way to keep it from loading the session I saved.  Thats what is cause the log on process to take forever.  As for the "Automatically save changes to session" option, it's never been turned on.

---

### Post by jdackle on 2007-08-31
> **thegibbling said:**
> But is there a way to keep it from loading the session I saved.  Thats what is cause the log on process to take forever.  As for the "Automatically save changes to session" option, it's never been turned on.

Sure! :)
1. Start that bloated session and close EVERYTHING you'd saved earlier so you get that clean *default* session you had before.
2. Close the session choosing to save it.

The next session you open will be as you want it... If I understood your problem correctly, that is! lol

---

### Post by thegibbling on 2007-08-31
Nope didn't seem to work.  I closed conky, beryl and saved the session again but it still seems to take forever to finish logging in.  Is there some way to blowout any saved sessions and revert back to when I used to have things load at startup.

---

### Post by ajgreeny on 2007-09-07
Sorry, been away for a few days.

Try backing up your ~/.gconf folder and then restarting the computer.  A new .gconf folder will be made which will I think have nothing added by you in the startup list.  If that works you can add back one by one and see if it get any quicker.

---

