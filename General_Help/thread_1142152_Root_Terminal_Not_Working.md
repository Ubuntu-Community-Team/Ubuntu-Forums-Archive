---
title: "Root Terminal Not Working"
date: 2009-04-28
forum: General Help
---

### Post by 9a8sy on 2009-04-28
Since I upgraded to version 9.04 from 8.1, I have not been able to open my Root Terminal. I click on it and it ask for a password, however after I enter it, it just closes out. Any suggestions to fix this?

---

### Post by dcstar on 2009-04-29
> **Frugalfart said:**
> Since I upgraded to version 9.04 from 8.1, I have not been able to open my Root Terminal. I click on it and it ask for a password, however after I enter it, it just closes out. Any suggestions to fix this?

It has a problem and is listed as a bug, change the launcher to this:

```
gnome-terminal -e "sudo -i"
```

---

### Post by 9a8sy on 2009-04-29
Seems to work when typing that into a regular terminal window. Is there anyway to insert that command into the Root Terminal Icon so it is automatic?

---

### Post by adult swim on 2009-04-29
right click applications, select edit menus.  then find root terminal, highlight it and choose edit.  then in the command box, remove whats in there and paste in what dcstar said.

---

### Post by maciu on 2009-04-29
That thing is pretty annoying, i am with Jaunty since Alpha 2 and there is no progress with this bug, now that so many ppl upgraded to jaunty launchpad gets flooded (together with my mailbox) with new duplicates of that bug. So there is hope for better. None of the temporary solutions presented neither here or other threads work, they all open a root terminal but every other new tab will be a "user" terminal :/ So far the best workaround for me was using terminator ( [https://launchpad.net/terminator](https://launchpad.net/terminator) ). The only problem with it is that it doesn't remember my preferences (IE keyboard shortcuts)... :/

---

