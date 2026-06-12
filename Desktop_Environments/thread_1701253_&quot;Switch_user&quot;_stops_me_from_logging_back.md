---
title: "&quot;Switch user&quot; stops me from logging back in"
date: 2011-03-06
forum: Desktop Environments
---

### Post by RobotGymnast on 2011-03-06
I installed a minimal Ubuntu build, and did the same with Gnome, so I'm liable to have some problems.

The current one is that when I'm at the login screen, and I click on a user account, it makes the "click" sound, and starts the little animation to the screen where I can enter the password. However, it gets cut short and flashes "error initiating conversation with au" (the rest of the text is cut off) and goes back to the original login screen.

Any help is appreciated.

---

### Post by RobotGymnast on 2011-03-10
Solved by removing the ```
@include common-pamkeyring
``` line from /etc/pam.d/gdm.

---

