---
title: "Windows not raising on focus"
date: 2006-08-02
forum: Desktop Environments
---

### Post by kjkrum on 2006-08-02
Lately my windows sometimes aren't raising when I focus them with a mouse click.  I have to focus the window on top and then focus the other one again to get it to raise.

Anybody else seeing this on Dapper?

---

### Post by Zalbor on 2006-08-02
That happens with me too, I have no idea how to fix it.
I assume it has to do something with the setting that new windows now don't jump to the foreground right away (which happened in Breezy and was annoying). Maybe making this caused a bug.

---

### Post by it.henrik on 2006-08-04
I have the same problem ... did this start to happen after you tried compiz? It did for me and someone else here in the forums.

Do you know how to fix it?

---

### Post by h00s on 2006-08-04
Same problem here.
When I run XGL-Gnome session, it works ok, but in non-XGL normal session, this behaviour occur.

Still waiting for solution then...:-(

---

### Post by thingy on 2006-08-04
See the attached screenie and let us know whether the "focus_mode" is set to click and the "raise_on_click" option is ticked.

i.e.

run gconf-editor and goto apps/metacity/general


jin

---

### Post by h00s on 2006-08-04
Yep, raise_on_click checked and focus_mode is click.

---

