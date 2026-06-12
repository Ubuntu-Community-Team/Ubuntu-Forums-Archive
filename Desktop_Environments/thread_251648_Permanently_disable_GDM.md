---
title: "Permanently disable GDM?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by vocaro on 2006-09-05
I am new to Ubuntu and am used to disabling automatic X Windows startup by changing the default runlevel (in /etc/inittab) from 5 to 3. Strangely, Ubuntu's default runlevel is 2, and yet it still forces me to run X Windows. How can I prevent this?

I had tried going to Administration > Services and turning off GDM, and that does the trick but only temporarily. If I reboot, GDM is back up and I'm again forced to run X Windows.

Thanks

---

### Post by jdong on 2006-09-05
**sudo rm /etc/rc2.d/S*gdm**

would do the trick.

---

### Post by aysiu on 2006-09-05
jdong's solution will probably work. You can also do ```
sudo aptitude remove gdm
``` if you want to make it *really* permanent.

---

