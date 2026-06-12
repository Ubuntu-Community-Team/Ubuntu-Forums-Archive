---
title: "Kubuntu 7.04 &quot;su returned with error&quot;?"
date: 2007-05-17
forum: Desktop Environments
---

### Post by 67GTA on 2007-05-17
I installed Kubuntu 7.04 and am getting error "su returned with error" or "conversation with su failed" when I attempt to open certain apps(gui) or click the administator mode button in certain apps. I also get this message with sudo in a konsole "sudo: timestamp too far in the future: May 17 17:18:02 2007". The time is 6:52 right now. I have only used Gnome until now. I have no idea why this is happening. Can someone help me fix this?

---

### Post by taurus on 2007-05-17
Reboot and try it again.

---

### Post by 67GTA on 2007-05-17
That done the trick. Thanks. Is this a bug or something I caused?

---

### Post by taurus on 2007-05-17
Not sure but perhaps don't run GUI apps with sudo as root.  Instead, use gksudo (for Gnome) and kdesu (for KDE).

---

