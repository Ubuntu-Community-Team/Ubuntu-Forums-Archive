---
title: "Windows - Can you change the C drive to X?"
date: 2009-04-20
forum: Desktop Environments
---

### Post by Maheriano on 2009-04-20
Is it possible to do that? The company I work for has a client that has some sort of Thin Client desktop system with 2 mapped network drives, X and Y. There is no C drive and they're trying to run our software but getting an error. We're trying to replicate the environment locally to reproduce the error but we can't figure out how to get rid of the C drive and replace it with a X drive. Is there a way to do it?

---

### Post by Darael on 2009-04-20
There's a tutorial on how to do it [here]("http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm").

Good luck.  I advise switching back when you're done, so that apps that use absolute paths rather than environment variables and were set up when the system drive was c: will work again.

---

### Post by Don1500 on 2009-04-20
Ahhh the good old days. Remember in DOS you could spoof the drive to be both. You could rename it X: and the cpu it would recognize the drive if you called for C: or X: in your software.

---

