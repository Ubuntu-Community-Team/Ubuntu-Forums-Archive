---
title: "Kate sessions"
date: 2006-02-11
forum: Desktop Environments
---

### Post by claydoh on 2006-02-11
I seem to be unable to figure out how to get kate to open files in the same session. it keeps opening files in a new session, and I got used to having it open files in a single session.

---

### Post by jeremy on 2006-02-12
Settings -> Configure Kate -> Sessions

---

### Post by Neo Ex on 2006-02-12
Open your ~/.local/share/applications/kde-kate.desktop (if you don't have it, copy the /usr/share/applications/kde/kate.desktop in ~/.local/share/applications and rename it kde-kate.desktop) and search for

Exec=kate %U

and change it like this:

Exec=kate --use

Now when you open a new file it will use the same Kate session. If this doesn't happen, try log out and re-login.

---

### Post by claydoh on 2006-02-12
Thanks! that took care of that, its the little things that make you pull your hair out, I guess :)

---

