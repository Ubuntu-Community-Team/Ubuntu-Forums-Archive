---
title: "Multiple processes"
date: 2009-09-17
forum: Desktop Environments
---

### Post by frobinson on 2009-09-17
When I first log in, my computer, a Pentium III, runs very slow. I open the system monitor and find that there are 29 processes of xfdesktop running. After closing 28 of them, things settle down. Can I keep from having the desktop open 29 times?

---

### Post by Brandon Williams on 2009-09-17
This isn't normal. You're going to want to try to figure out what all those extra xfdesktop processes are doing and how they got started.

Do all of the processes have the same parent PID? If so, is it the PID of xfce4-session? If it's not the same parent PID, then what are the parent processes?

If you can figure out what the parent process(es) is(are), it will be easier to figure out how to make the extra instances _not_ start.

---

