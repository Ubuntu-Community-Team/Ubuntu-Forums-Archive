---
title: "Unexpected Kernel Update"
date: 2006-08-04
forum: Desktop Environments
---

### Post by andb on 2006-08-04
This morning the update manager listed a kernel update as being available. Its the same kernel, at least as far as the number, as the one I already have. This has happened once before. Is this kernel different then the one I have currently installed or is this an update manager bug?

---

### Post by SishGupta on 2006-08-04
I'm no pro (infact i'm very new), but i think that they were just kernel headers with the same version numbers. I am not sure what the changes were because they were not listed.

---

### Post by OpsVentus on 2006-08-04
Is it the exact same number? Can you post the 2 full names?
If so it's an update manager bug.

Cheers,
Bart.

---

### Post by SishGupta on 2006-08-04
Here maybe this link will answer your question:

[http://www.ubuntuforums.org/showthread.php?t=228445](http://www.ubuntuforums.org/showthread.php?t=228445)

---

### Post by andb on 2006-08-04
SishGupta got it right, It was that security update. I have kernel 2.6.15-26.45 and its ...46 that wants to install. What threw me was that the kernel names drop the last bit of info, and when i did uname -r, also the last part is dropped. It bugged me that the package name was the same, but indeed, it is a new version. Now I can go back to trusing the update manager ;)

---

