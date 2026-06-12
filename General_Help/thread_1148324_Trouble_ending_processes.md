---
title: "Trouble ending processes"
date: 2009-05-04
forum: General Help
---

### Post by psychobillyjekyll on 2009-05-04
Hello all,

When I am running Xubuntu Jaunty, certain processes won't end when the program is closed. X-moto is one main culprit here. I checked my system monitor and there were four sleeping xmoto processes. The program hangs on the quit command, I've given it over half an hour to close in the past, which on a centrino core 2 duo with 3 GB of RAM is extreme overkill. I have cleared the programs off my desktop with the 'xkill' command, which I know only gets rid of the image of the process, not the process itself. I was wondering if anybody else is dealing with this issue, or even better if somebody has a solution to it.

Thanks
Justin

---

### Post by CatKiller on 2009-05-04
> **psychobillyjekyll said:**
> I have cleared the programs off my desktop with the 'xkill' command, which I know only gets rid of the image of the process, not the process itself. 

No it doesn't. It kills the process that created the window that you select. You can do the same manually. **killall xmoto** in this case. If they still won't die, you can look up the process ID number (PID for the process you want to kill, and use **kill -9 <PID>.**

---

### Post by psychobillyjekyll on 2009-05-16
Thanks for the clarification. I was wondering if there was someway to modify the system so that it would kill any process in futex_wait status for over a set amount of time?

---

### Post by sgosnell on 2009-05-16
You can add the Force Quit button to a panel, and get rid of unresponsive programs fairly easily.  You just click on the button, then the non-responding program, and it's killed.

---

