---
title: "Anacron vs. Cron: What's the difference?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by dbeckham32 on 2005-08-04
Okay, I've figure out to create my own crontab to run scripts and applications, and even log the result to a text file. So I feel I know how to use cron and crontab.

But what does Anacron do and how does it differ? I've read the MAN and INFO pages, but I must be missing something because I'm not sure of the difference.

Is there a tutorial available on Anacron? I have not seen one as of yet.

Thanks in advance.

---

### Post by Juergen on 2005-08-04
Cron starts your processes only if the box is powered-on at the time you want to execute something.

Anacron looks at boot-time if something was missed while the computer was off.

You might want to move your stuff in your crontab to the anacrontab, and just start anacron peoridically via cron (in case you left the box running)

---

