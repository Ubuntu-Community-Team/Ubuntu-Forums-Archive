---
title: "Can't renice processes spawned with batch"
date: 2009-04-30
forum: General Help
---

### Post by lazer on 2009-04-30
I often use batch as a rudimentary load leveler for queuing simulation runs in my office (programs written in FORTRAN and C by me).  I recently upgraded to 8.04 from 7.10.  Processes spawned by batch are given the priority level 4.  I would then use renice to set the priority level to 0 (which worked since I was still the owner of the process).  After upgrading however I apparently can't change the priority of processes spawned with batch even if I'm the owner of the process.  I can still change the priority of processes spawned from a terminal.  Here's a sample from the command line.

```

lazersos@dust:~/Sims/denisis$ ps -A | grep "dust"
31571 pts/2    00:49:44 dust_ball
32208 ?        00:30:50 dust_ball
lazersos@dust:~/Sims/denisis$ renice 0 -p 31571
31571: old priority 0, new priority 0
lazersos@dust:~/Sims/denisis$ renice 0 -p 32208
renice: 32208: setpriority: Permission denied
lazersos@dust:~/Sims/denisis$ atq
1       Thu Apr 30 12:24:00 2009 = lazersos

```

One copy is running from the command line (pts/2) which I can change priority on.  The other has been spawned by batch, and batch knows I'm the owner but renice won't let me change the priority.  This used to work.  Also if anyone knows how to set force batch to run a command with priority 0 (from the batch script itself) I'd appreciate it (nice doesn't work).

---

### Post by lazer on 2009-04-30
Anyone?  From talking to some of the other linux guru's here this may well be a bug.

---

### Post by lazer on 2009-05-01
Maybe someone could tell me how to use ubuntu-bug to submit this.  As the bug is with a command line utility it appears (not sure if the problem is with renice or batch).

---

### Post by lazer on 2009-05-23
Just bumping this to see if anyone else has experienced this.

---

