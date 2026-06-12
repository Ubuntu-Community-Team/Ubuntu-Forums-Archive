---
title: "Odd problem"
date: 2009-06-03
forum: General Help
---

### Post by papabill on 2009-06-03
Very odd problem:

I just installed Ubuntu 8.04.1 on an HP Pavillion, and when I double-click anything, it shows the "Starting ..." in the task bar for a moment, then goes completely away. And no program starts. I've rebooted, and still nothing.

Ever heard of this?

Thanks

---

### Post by michy99 on 2009-06-03
Try starting a program from the terminal and see what errors you get.

---

### Post by uidb4056 on 2009-06-03
> **papabill said:**
> Very odd problem:

I just installed Ubuntu 8.04.1 on an HP Pavillion, and when I double-click anything, it shows the "Starting ..." in the task bar for a moment, then goes completely away. And no program starts. I've rebooted, and still nothing.

Ever heard of this?

Thanks
Have you updated your system after install, if not go to menu Sytem-Administration-Update mangar and see if after applying the updates and restart still happens.

---

### Post by DeMus on 2009-06-03
> **papabill said:**
> Very odd problem:

I just installed Ubuntu 8.04.1 on an HP Pavillion, and when I double-click anything, it shows the "Starting ..." in the task bar for a moment, then goes completely away. And no program starts. I've rebooted, and still nothing.

Ever heard of this?

Thanks

Yes. I have had this phenomenon also, but only when the cpu is too busy to really start a new task.
Please open a terminal (menu Applications - Accessories - Terminal) and type top in it.
You will see a list of programs running at this moment. The one on top is the one which eats most of the cpu power.
To stop top simply type a q.
This way you know why the cpu is so busy. Maybe we can do something about it.

---

### Post by kestrel1 on 2009-06-03
Instead of double clicking on a program, can you open a terminal & type the command to start the program. This may give a clue as to what is going on. Will the terminal actually open?

---

### Post by papabill on 2009-06-03
Sorry, my mistake. I was warm booting and nothing happened. I cold booted and all seems to be well.

Thanks, sorry to bother you.

---

