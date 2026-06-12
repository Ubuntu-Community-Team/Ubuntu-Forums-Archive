---
title: "One-time cron job"
date: 2011-02-15
forum: Desktop Environments
---

### Post by lucacerone on 2011-02-15
Dear all,
I've a question.
Due to the maintenance policy of my university,
my computer (ubuntu 10.04 on it) will need to be rebooted tomorrow to
gain the new ip-address.

It is just a curiosity, I'd like to know if it's possible
to set a one-time cron job.

I'd like that tomorrow at 9 my computer would reboot and after that
the job is no longer executed.

Is this possible?
Thanks a lot for your help.
Cheers, -Luca

---

### Post by anglican on 2011-02-15
> **lucacerone said:**
> Dear all,
I've a question.
Due to the maintenance policy of my university,
my computer (ubuntu 10.04 on it) will need to be rebooted tomorrow to
gain the new ip-address.

It is just a curiosity, I'd like to know if it's possible
to set a one-time cron job.

I'd like that tomorrow at 9 my computer would reboot and after that
the job is no longer executed.

Is this possible?
Thanks a lot for your help.
Cheers, -LucaFor a one-off "at" is what you need, not cron.

H

---

### Post by lucacerone on 2011-02-15
thanks!

---

### Post by lucacerone on 2011-02-15
Sorry just the last help:
I've tried to run a test using
> 
at -m 11:01 AM FEB 15 2011 < 'echo "test" > home/luca/Desktop/atlog'

But this way it doesn't work.
How can I create a file at a given time?
Thanks a lot for your help,
Cheers, -luca

---

### Post by anglican on 2011-02-15
> **lucacerone said:**
> Sorry just the last help:
I've tried to run a test using

But this way it doesn't work.
How can I create a file at a given time?
Thanks a lot for your help,
Cheers, -lucaI've only used at to run scripts e.g.
```
at -f /path/to/script -v 11:15
```so I'm no expert in using it. BTW you can always run shutdown with a time e.g. ```
shutdown +1440 -r
``` to reboot in 24 hours time.

H

---

### Post by Rhubarb on 2011-02-15
> **lucacerone said:**
> How can I create a file at a given time?
Thanks a lot for your help,
Cheers, -luca

Try this one out:
```
echo "echo 'test' > ~/testing.txt" | at 22:31
```

This will also work:
```
echo "echo \"test\" > ~/testing.txt" | at 22:33
```

And I'm sure there's plenty of other ways of getting it to work too.

---

