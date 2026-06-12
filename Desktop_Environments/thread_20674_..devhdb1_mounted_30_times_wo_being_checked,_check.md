---
title: "../dev/hdb1 mounted 30 times w/o being checked, checked forced..."
date: 2005-03-17
forum: Desktop Environments
---

### Post by yoha on 2005-03-17
Hi folks,
   I receive the following error this morning when i boot the box "/dev/hdb1 has been mounted 30 times without being checked, checked forced" . It then goes on to check the partition similar to windows' chkdsk. The message was shown during the very early initialization process. This has happened twice. I am not sure what causes the error to be generated. the hdb1 is the partition where i install ubuntu and it does not share any other os in it and my box is regularly turned on during the day and only is shutdown at night. any thoughts || suggestions?

-yoha

---

### Post by jeremy on 2005-03-18
This isn't an error, it happens automatically.

---

### Post by bored2k on 2005-03-18
[QUOTE=jeremy]This isn't an error, it happens automatically.[/QUOTE]
 Quite cool IMHO. The beauty of automation.

---

### Post by yoha on 2005-03-18
[QUOTE=bored2k]Quite cool IMHO. The beauty of automation.[/QUOTE]
 so are you guys saying at one time randomly for some reasons instructed by the kernel, my hdb1 was mounted and unmounted for 30 times? sorry i dont understand how can this be "automation". can you explain automation in this context? isnt it impossible for hdb1 to be unmounted when it is being used? my box runs all the time during the day.

-yoha

---

### Post by bored2k on 2005-03-18
[QUOTE=yoha]so are you guys saying at one time randomly for some reasons instructed by the kernel, my hdb1 was mounted and unmounted for 30 times? sorry i dont understand how can this be "automation". can you explain automation in this context? isnt it impossible for hdb1 to be unmounted when it is being used? my box runs all the time during the day.

-yoha[/QUOTE]
 No no hold your horses there.

Every 30 time you start your computer , wether its a restart or whatever, Linux has to mount your drive right ? So on every 30 mounts it checks itself for consistencies.

---

### Post by yoha on 2005-03-18
[QUOTE=bored2k]No no hold your horses there.

Every 30 time you start your computer , wether its a restart or whatever, Linux has to mount your drive right ? So on every 30 mounts it checks itself for consistencies.[/QUOTE]
 aha.... now it's clear "every 30 time you start your computer". Thanks!

---

### Post by missmoondog on 2005-12-08
searched and found this thread. i get same message, but it says after 20 times on mine. has only ever happened on this particular computer (twice) i'm on now. i have 4 others setup the exact same way, that have never done this check.  my main computer is restarted more often than this one and one other computer is restarted at least as often also. is there a way to disable it that i might have done on accident? if so, how do i re-enable it?

Edit:
just noticed the thread title. i'm running 5.10 breezy.

thank you

---

