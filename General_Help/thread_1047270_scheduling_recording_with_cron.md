---
title: "scheduling recording with cron"
date: 2009-01-22
forum: General Help
---

### Post by davidtuti on 2009-01-22
Hi,

I have an script where when I select an option, it gives me a date an a hour. This date and hour I have to schedule with for instance, crontab, to execute a command.

I would like to can modify the the crontab from my script. That it's possible?

Could you help me?

Many thanks!

---

### Post by sedawk on 2009-01-22
What you are looking for is the tool called "at", not "cron".

Example:

```

# shutting down in 10 minutes 
echo "/usr/sbin/shutdown -h now" | at now + 10 minutes
# delete file /tmp/xyz at 11:00 pm
echo "rm /tmp/xyz" |at 23:00
# check the existing jobs
atq
1 ...
2 ...
# Remove job "1" with atrm
atrm 1

```

You can pipe a full script to the at command with
"at now + 10 minutes <script", but I recommend to use something
like "echo "/bin/bash script" | at now + 10 minutes"

(I have implemented a digital VCR that works differently.
 In cron there is a tool I start every minute that reads the list
 of future recordings from a config file and starts recording when
 needed).

---

### Post by davidtuti on 2009-01-22
> **sedawk said:**
> What you are looking for is the tool called "at", not "cron".

Example:

```

# shutting down in 10 minutes 
echo "/usr/sbin/shutdown -h now" | at now + 10 minutes
# delete file /tmp/xyz at 11:00 pm
echo "rm /tmp/xyz" |at 23:00
# check the existing jobs
atq
1 ...
2 ...
# Remove job "1" with atrm
atrm 1

```

You can pipe a full script to the at command with
"at now + 10 minutes <script", but I recommend to use something
like "echo "/bin/bash script" | at now + 10 minutes"

(I have implemented a digital VCR that works differently.
 In cron there is a tool I start every minute that reads the list
 of future recordings from a config file and starts recording when
 needed).


But... when at if I reboot the system doesn't clean the programmings??

Thanks,

---

### Post by sedawk on 2009-01-23
Hello!

The job list of at is not changed by a reboot!

As long as the system is up and running at the given time
it will execute the given job.

---

