---
title: "[SOLVED] kicker no longer autostarts"
date: 2007-12-26
forum: Desktop Environments
---

### Post by TeeAhr1 on 2007-12-26
and darned if I know why.  I added a link to it to ~/.kde/Autostart, which works, but why would that have happened in the first place??

---

### Post by TeeAhr1 on 2007-12-26
SOLVED it myself.

In the ~/.kde/share/autostart directory, there was a file called panel.desktop.  I tried to run it, and it errored out saying the file had no type= entry.  I tried to give it Type=kicker, which didn't work, but I'm sure if I knew the syntax, it'd be trivial.  What I did then was took the link that I had previously put in ~/.kde/Autostart into ~/.kde/share/autostart, and deleted the panel.desktop file.  This works, and has the added bonus of starting kicker noticeably faster than before.

-pd.

---

### Post by ferd on 2007-12-29
> **TeeAhr1 said:**
> SOLVED it myself.

In the ~/.kde/share/autostart directory, there was a file called panel.desktop.  I tried to run it, and it errored out saying the file had no type= entry.  I tried to give it Type=kicker, which didn't work, but I'm sure if I knew the syntax, it'd be trivial.  What I did then was took the link that I had previously put in ~/.kde/Autostart into ~/.kde/share/autostart, and deleted the panel.desktop file.  This works, and has the added bonus of starting kicker noticeably faster than before.

-pd.

Thank you. This works for me when nothing else did except the terminal.:guitar:

---

### Post by TeeAhr1 on 2007-12-30
Glad I could help!

-p.

---

