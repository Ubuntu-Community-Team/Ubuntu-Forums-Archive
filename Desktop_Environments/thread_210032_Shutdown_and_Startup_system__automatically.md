---
title: "Shutdown and Startup system  automatically"
date: 2006-07-06
forum: Desktop Environments
---

### Post by mfaridi on 2006-07-06
We have a ubuntu 6 system so that my system need turn off and turn on properly before users start working on next day. But my trouble is how can i take the system (ubuntu) turn off and turn on in specifiy time.
Example:
- Time turn off/shutdown server:
at 3:00am July-03-2006

- Time turn on/startup server:
at 7:00am July-03-2006

How can i do this on ubuntu system? Do my server support auto wake up ?

---

### Post by scxtt on 2006-07-06
i doubt that'll have anything to do w/ an OS - i think that'll be BIOS related ... i think my mb does something like that ... seriously though, who wants an OS that can power their box on? -- not me -- when i say "log out" **i mean it** :p ...

---

### Post by hayesey on 2006-07-06
Is just leaving it on all the time not an option?  My servers only reboot when I do a kernel upgrade or something similar.

As said, automatically powering up would be a job for the BIOS.  The OS can only do anything when it's actually running!  Have a look for any likely settings in your BIOS settings.

---

### Post by hda on 2006-07-06
automatic shutdown using cron:

```
sudo crontab -e
```

insert a line like this

```
0 3 * * * /sbin/shutdown now
```

to shutdown your system every day at 3.00am

To do an automatic poweron you have to use the BIOS settings, as mentioned before.

_hda_

---

### Post by Ramses de Norre on 2006-07-06
The turn off thing is possible though, you can create a cron job for it. I'd have to search a bit on how to do that.

---

### Post by mfaridi on 2006-07-09
> **hda said:**
> automatic shutdown using cron:

```
sudo crontab -e
```

insert a line like this

```
0 3 * * * /sbin/shutdown now
```

to shutdown your system every day at 3.00am

To do an automatic poweron you have to use the BIOS settings, as mentioned before.

_hda_

I use your guide but it does not work
crontab can not shutdown my system automatically

---

### Post by 5-HT on 2006-07-09
> **mfaridi said:**
> I use your guide but it does not work
crontab can not shutdown my system automatically

Instead of passing the command directly to cron, having cron execute a shutdown script should work.

1. Make a simple script (named 'bar' in this example saved in /home/foo/) containing the following:
```
#! /bin/bash
shutdown -h now 
``` 
2. Make the script executable:
e.g., ```
chmod +x /home/foo/bar 
``` 
3. Add the relevant entry to root's crontab*:
e.g., ```
 sudo crontab -e 
``` ```
0 3 * * * /home/foo/bar 
``` 
*The example will run the script at 0300h. To view the crontab syntax for changing the time(s) the script is run see the crontab(5) manual:
```
 man 5 crontab 
``` 


Hope that helps

---

### Post by galileon on 2006-07-16
for the startup, i use my bios option - wake on realtime clock alarm, and set the date and time

i havent tried the shut down yet

---

