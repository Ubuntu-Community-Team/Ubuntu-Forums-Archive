---
title: "kde session - excluding applications from being saved"
date: 2007-12-12
forum: Desktop Environments
---

### Post by umuro on 2007-12-12
I want to exclude certain applications from being saved into kdmserverrc.  I do not want them to autostart next time because they were just there.

How?

---

### Post by GeneralZod on 2007-12-12
I've never tried it myself, but have you tried 

System Settings -> Advanced -> Session Manager 

and then listing the applications in the "to be excluded" list?

---

### Post by ajgreeny on 2007-12-12
If you mean things that were open when you shutdown, or logged out, just chose to start with a new empty session on boot up. The setting used to be in the "Sessions" section of kcontrol, but I don't know about the newer kde desktop; it must be there somewhere.  You can then add anything you do want to start at boot time to the ~/.kde/Autostart folder.

---

