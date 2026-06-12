---
title: "Empty Trash - Sudo Required?"
date: 2009-03-27
forum: General Help
---

### Post by Spectre5 on 2009-03-27
Is there any way to lock the trash/recycle bin in Ubuntu?  I don't mean lock it to the panel, I mean lock it so that only sudo can empty the trash.

I know this sounds weird, but here's my line of thinking.  If someone were to (hack) into my user account via SSH (but did not know the password into the root account), then that person could not mess the system up (much).  But they could delete all of my files in my home directory.  If the trash was locked, I could restore these files without them being "lost forever."

---

### Post by ddrichardson on 2009-03-28
The trash is provided by nautilus, if they ssh'd into a terminal then they'd bypass the trash anyway.

---

### Post by ethoxyethaan on 2009-03-28
rm <file>

bypasses trash

---

### Post by Spectre5 on 2009-03-29
Hm...I guess I didn't think about/realize that "rm" bypasses the trash.  Ok...well never mind then, thanks!

---

### Post by DeMus on 2009-03-29
> **Spectre5 said:**
> Hm...I guess I didn't think about/realize that "rm" bypasses the trash.  Ok...well never mind then, thanks!

> If someone were to (hack) into my user account via SSH (but did not know the password into the root account)

If somebody could hack your user account they have hacked your password, which is also the sudo password since sudo uses your password. Or do you log in with a username which is not sudo capable?

---

### Post by Spectre5 on 2009-03-29
> **DeMus said:**
> If somebody could hack your user account they have hacked your password, which is also the sudo password since sudo uses your password. Or do you log in with a username which is not sudo capable?

Of course I would have used another account without root privileges :)

---

