---
title: "simple question about cron"
date: 2009-02-10
forum: General Help
---

### Post by Memes11 on 2009-02-10
Hello,

I set up a task to be done everyday at 12:00, what will happen if I start my computer at 13:00? will the task will run as it should be done at 12:00? or will the task be skipped as it is too late already?

If the answer is the first proposal above, then what happen after 3 days switched off? execute 3 times the task? I do not think so, but I prefer to ask to be sure

Actually, I wish to synchronize one folder with my NAS using unison, I do not want RAID as there is only one folder.

---

### Post by ju2wheels on 2009-02-10
No it would be skipped and only triggered when its 12 again.

---

### Post by Memes11 on 2009-03-31
Thanks for the info

---

### Post by dcstar on 2009-03-31
> **Memes11 said:**
> Hello,

I set up a task to be done everyday at 12:00, what will happen if I start my computer at 13:00? will the task will run as it should be done at 12:00? or will the task be skipped as it is too late already?
........

Ubuntu uses Anacron, have a look at the man page.

---

### Post by measekite on 2009-04-08
> **Memes11 said:**
> Hello,

I set up a task to be done everyday at 12:00, what will happen if I start my computer at 13:00? will the task will run as it should be done at 12:00? or will the task be skipped as it is too late already?

If the answer is the first proposal above, then what happen after 3 days switched off? execute 3 times the task? I do not think so, but I prefer to ask to be sure

Actually, I wish to synchronize one folder with my NAS using unison, I do not want RAID as there is only one folder.

Along similar lines:

Let say you have two tasks.  TaskA is scheduled at 1 and TaskB is scheduled as 1:30.  If TaskA begins on time and takes 45 minutes to complete (1:45) will TaskB start even though it was delayed by TaskA.

---

