---
title: "Rebooting in Ubuntu"
date: 2009-02-06
forum: General Help
---

### Post by philidox on 2009-02-06
Why is that from the GUI interface of ubuntu I can click go to "system>>>quit" and click on reboot and the system reboot without a password prompt BUT if I type reboot in the CLI it must be proceeded with sudo and I'm force to enter in password?  What command is being executed when I restart the computer via GUI?

---

### Post by kanikilu on 2009-02-06
Someone else may have more details, but my best guess is that when you use the GUI, essentially GDM is running the shutdown command, and since the GDM process is already running under root, it doesn't ask for a password.

---

