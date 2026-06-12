---
title: "stop the boot (startup) process"
date: 2009-07-09
forum: Desktop Environments
---

### Post by cccc on 2009-07-09
hi

Howto stop the boot (startup) process from Ubuntu Jaunty using keyboard to see all warning messages on the screen?

btw. I know, System Protokoll: kern.log or enable BOOTLOGD, but I'm only interested to stop the system during startup.

---

### Post by kpkeerthi on 2009-07-10
When you system boots and GRUB is about to load, press 'Esc' key to view the Menu. Select the 'Kernel' boot line and Press 'e'. Scroll to the end and remove the word 'splash'. Press 'Esc'. Now press 'b' to boot. If you need to see more verbose boot text, delete the word 'quiet' from the Kernel line as well.

---

### Post by cccc on 2009-07-10
**CTRL-S** to stop 

and 

**CTRL-Q** to resume

solved this problem!

---

