---
title: "Missed cron items"
date: 2007-08-01
forum: Desktop Environments
---

### Post by AndyPopely on 2007-08-01
I have 2 problems which I'm wondering whether they're being caused by the same issue.  

The 2 problems are (1) system logs not being rotated and (2) not being notified of system updates.

Are both of these controlled by functions which are expected to run at specific times ?  If so what options do I have to automatically run missed functions on a Feisty Fawn system that isn't up and runing very often ?

---

### Post by AndyPopely on 2007-08-03
Solved ... the problem was anacron wasn't being scheduled ... I installed and ran sysv-rc-conf and reinstated anacron being scheduled and it fixed both problems.

---

