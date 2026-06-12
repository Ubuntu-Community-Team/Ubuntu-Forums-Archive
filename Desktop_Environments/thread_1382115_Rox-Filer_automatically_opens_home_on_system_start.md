---
title: "Rox-Filer automatically opens /home on system startup"
date: 2010-01-15
forum: Desktop Environments
---

### Post by O-pos on 2010-01-15
Hello, I replaced Gnome Nautilus with Rox-Filer as described in this howto: [http://ubuntuforums.org/showthread.php?t=48169](http://ubuntuforums.org/showthread.php?t=48169)

Everything went well and I also solved automatic mounting issues.

The remaining problem is that every time I start the system (Ubuntu 9.10), Rox-Filer opens autopmatically displaying home folder.

Is there a way to turn this off?

---

### Post by ajgreeny on 2010-01-15
For a single shutdown, go to Startup applications, options tab, and set to "remember applications open on shutdown".  Now close all applications and shutdown or restart.  Now do the same in reverse in the Startup applications options tab, and deselect the "remember" option.  All should now be OK if rox-filer acts like nautilus.

---

### Post by O-pos on 2010-01-16
Thanks, I tried but it did not help. I don't understand why because Rox-filer is supposed to act like Nautilus.

---

