---
title: "Cron  job issue"
date: 2009-06-18
forum: General Help
---

### Post by beekr on 2009-06-18
Hey all,

I got a script that I would like to have run every minute. I have added it in cron:

>  */1 * * * * /bin/turn 

I have checked the .Xauthority 

>  -rw------- 1 mike mike 121 2009-06-17 20:49 .Xauthority  

I checked syslog and it looks like it is running, but my script never runs

>  Jun 17 21:26:01 tuxlap-01 /USR/SBIN/CRON[10789]: (mike) CMD (/bin/turn) 

I checked the script and it's executable

>  -rwxrwxrwx 1 mike mike 1329 2009-06-17 09:48 /bin/turn 

I can run the script manually and it works perfectly. Is there something I'm missing ? Thanks in advance.

~Beekr

---

