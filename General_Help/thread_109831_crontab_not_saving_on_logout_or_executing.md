---
title: "crontab not saving on logout or executing"
date: 2005-12-29
forum: General Help
---

### Post by three_sixteen on 2005-12-29
So I used crontab -e to add a job to run a perl script every 5 minutes.

```
5,10,15,20,25,30,35,40,45,50,55,59 * * * * perl "/path/to/perl/script.pl"
```

I waited 5 minutes for the script to execute but nothing happened, and I figured maybe if I logged out and back in that the script would run... but when I did a crontab -l to list the job I added it said that I had no crontab file.

What am I doing wrong?

---

### Post by Stereotypical Rage on 2005-12-29
When I run a crontab, I have a crontab file setup somewhere on my PC.

I have it at /home/$my_user_name/Cron/cron.txt

Then I type: sudo crontab -u USERNAME /path/to/file

Need to have the cron daemon running too.

---

### Post by three_sixteen on 2005-12-29
[QUOTE=Stereotypical Rage]When I run a crontab, I have a crontab file setup somewhere on my PC.

I have it at /home/$my_user_name/Cron/cron.txt

Then I type: sudo crontab -u USERNAME /path/to/file

Need to have the cron daemon running too.[/QUOTE]

The cron daemon is running, do I need to do that crontab thing every time I log in or is there a way to make it stick when I log in?

I'm still not sure why the file isn't sticking..

---

