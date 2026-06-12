---
title: "anacron script problem"
date: 2009-03-19
forum: General Help
---

### Post by iopo on 2009-03-19
Hi everybody,

I tried to schedule an automatic backup with anacron. The script I wrote works fine when I run it, but if I check my system log, it says:

anacron[5963]    Job `backupdocs' started
anacron[5963]    Job `backupdocs' terminated (exit status: 127).

Exit status 127 means command not found.
But how comes that if I run it it works with no problem, but when anacron runs it there are problems?

Today I tried something new; I changed the name of the job in anacrontab and I restarted anacron with a 

> sudo anacron

well, it ran my script without problems! This is weird!

I attach my script.

Thanks a lot!

---

### Post by foolishchild on 2009-04-05
anacron jobs run as root. can you run your backup job as root, from the ~root directory?

---

### Post by iopo on 2009-04-06
Thanks for the reply! I was already thinking my question got lost in the forum.

Anyway, I can run the script manually both as normal user, and as sudo, both from my home directory, and copying the script into ~root and running it from there. In all these situations everything works without a problem.

I also copied the scripts into my ~root directory and change the path in the anacrontab file to point at the ~root location. Again, when it is time to run the script it says "exit status: 1". I'm not sure what kind of error it is, but I know it means the script has not been run.

For your information, here is my anacrontab.

Thanks a lot

---

