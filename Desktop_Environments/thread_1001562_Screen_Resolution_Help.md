---
title: "Screen Resolution Help"
date: 2008-12-04
forum: Desktop Environments
---

### Post by l33tsp33k3r on 2008-12-04
Im running Ubuntu Version Hardy Heron on my computer, but the resolution went berserk on me! If I log on, I cannot see anything, and I can't see enough to change the screen resolution. =( If there is a way to change the resolution from the kernel or something I need to know about, could someone please tell me? I really need some help! Please post!

---

### Post by stefangr1 on 2008-12-04
What you could do is:
1 push Ctrl+Alt+F1
2 login
3 execute "sudo nano /etc/X11/xorg.conf"
4 change your monitor frequency and resolution in the monitor section. If you don't immediate see a setting that is clearly wrong, have a look here: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Swagman on 2008-12-04
At boot time.. When grub comes up... press Esc.

Select recovery...When that finishes you will be left at a box with a few options... Choose the bottom one X-server (or something like that).

When thats finished choose reboot.

My cousin had this problem with Gutsy Gibbon.. Turns out he had switched his computer on before the monitor and it dropped the resolution into a kind of "safe mode"

---

