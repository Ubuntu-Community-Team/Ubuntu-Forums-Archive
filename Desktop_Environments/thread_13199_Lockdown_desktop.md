---
title: "Lockdown desktop"
date: 2005-01-29
forum: Desktop Environments
---

### Post by ubuntu1 on 2005-01-29
I've setup my 79 year old father with his first computer, running Ubuntu of course. He's doing well, browsing the web, writing e-mail and some word processing. However he does have the habit of panicing and losing the desktop launchers and panels. Is there a way to lock down the desktop to stop him changing things?

Thanks

---

### Post by valadil on 2005-01-29
You can copy his home directory (or specifically hist .gnome2 folder and whichever other ones are relevant).  Then restoring it is easier.  Maybe you could write a script in /etc/rc2.d that copies the backed up settings back to his home dir on each reboot?

---

