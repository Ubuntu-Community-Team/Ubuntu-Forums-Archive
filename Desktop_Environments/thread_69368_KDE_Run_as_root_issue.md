---
title: "KDE Run as root issue"
date: 2005-09-26
forum: Desktop Environments
---

### Post by jej2003 on 2005-09-26
I am new to Kubuntu (and kde 3.4) and am having some issues with running items as root from the application menu.  If I run Kynaptic it works fine after logging in with the root password, but if I close it and try to restart kynaptic the application simply does not start.  I have noticed the same issue with kuser as well.  If I wait some time I can then reopen kynaptic and kuser but there is a period of time where I can't, anyone have any clue how to fix this?

---

### Post by mlomker on 2005-09-26
>  If I wait some time I can then reopen kynaptic and kuser but there is a period of time where I can't, anyone have any clue how to fix this?

Haven't seen that.  You can try typing **sudo killall kynaptic** at a prompt the next time that happens and see if it fixes it.

---

### Post by jej2003 on 2005-09-26
kynaptic: no process killed
 is what I get when I run that command, but if I do a ps -ef | grep kynaptic there are 2 instances running.  Killing them does not help either though....does anyone have any other ideas?

---

### Post by aysiu on 2005-09-26
How exactly are you running Kynaptic as root? Have you tried running the command *kdesu kynaptic*?

---

### Post by jej2003 on 2005-09-28
I am running it right from the start menu.  When I do kdesu kynaptic it asks for the password and again just freezes.  There are no errors thrown

---

