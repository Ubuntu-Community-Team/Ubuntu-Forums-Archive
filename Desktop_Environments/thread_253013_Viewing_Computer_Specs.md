---
title: "Viewing Computer Specs"
date: 2006-09-07
forum: Desktop Environments
---

### Post by OtubrabNad on 2006-09-07
How can I view the specs of my computer? I'm talking about the kind of information that you'd find under System in the Windows control panel. I tried using ubuntu's device manager, but just about everything it lists is "unknown." Thanks.

---

### Post by duff on 2006-09-07
I don't know of any GUI programs, but almost everything you'd want is located in the **/proc** directory.  For example, running ```
# cat /proc/cpuinfo
``` shows information about all the processors in your computer.  Run **man proc** for information about what the other files tell you.

---

