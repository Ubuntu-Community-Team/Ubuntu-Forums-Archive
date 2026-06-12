---
title: "How do I set the hidden attribute on a file or folder?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by pubwho on 2006-06-12
I want to hide a folder, how do I set the hidden attribute?

---

### Post by johnc4510 on 2006-06-12
If the file is in your home folder, rename it
Example:change screensaver to .screensaver

---

### Post by pubwho on 2006-06-12
That's worked, but now my file associations are messed up. Anything that references  the folder can no longer find it.

Is there an equivalent to the DOS attrib command in Linux?

eg:

attrib +h filename.ext

---

### Post by Ahriman on 2006-06-12
[QUOTE=pubwho]That's worked, but now my file associations are messed up. Anything that references  the folder can no longer find it.

Is there an equivalent to the DOS attrib command in Linux?

eg:

attrib +h filename.ext[/QUOTE]

You will have to change the references to include the . before the directory name. AFAIK there isn't any command like the attrib command from DOS to do what your asking, altho I could be wrong

---

