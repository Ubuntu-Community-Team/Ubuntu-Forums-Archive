---
title: "Odd issue with cron"
date: 2005-12-11
forum: General Help
---

### Post by barryso on 2005-12-11
Does anyone know about cron oddities in Ubuntu?

I have cron jobs each night that capture radio streams with streamripper.  These jobs have been running perfectly on a Debian Sarge computer for several months.  They also seem happy on a Suse 10.0 build.  

I tried using the same calls on an Ubuntu Breezy build and it gets strange.  Streamripper starts and runs for about 4 or 4.5 minutes.  Then streamripper stops.  

Oddly, running the jobs from the command line works fine, it only pulls this shut down trick when running from cron.  

Searching these forums turned up ideas for setting the path in crontab and playing with the ulimit settings.  Neither of these have produced any changes in the behavior of the streamripper jobs.  Oddly, the ulimit settings of root are exactly the same on the Ubuntu and the Suse builds yet it works on Suse.

Any help you could provide is greatly appreciated. I've been googling and searching for a long time now and haven't found the fix.

Many thanks.

---

### Post by Zelut on 2005-12-11
I am having problems with my cronjobs as well.  Sorry I don't have a fix, but I wanted to tag into this thread to (hopefully) find an answer as well.

I run a few commands thru cron for my webserver--which never work--unless I do them manually.  Can anyone tell me if these look syntaxically correct?

```
30 00 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/logs.php &> /dev/null
59 23 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/ftp_logs.php &> /dev/null
59 23 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/mail_logs.php &> /dev/null
59 23 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/cleanup.php &> /dev/null
0 4 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/webalizer.php &> /dev/null
0,30 * * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/check_services.php &> /dev/null
15 3,15 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/quota_msg.php &> /dev/null
40 00 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/traffic.php &> /dev/null

```

---

### Post by barryso on 2005-12-12
>> 30 00 * * * /root/ispconfig/php/php /root/ispconfig/scripts/shell/logs.php &> /dev/null

These look ok to me and somebody with extensive php experience could confirm it.  

Is this running from a users crontab (started with "crontab -e") or from /etc/crontab?  


The /etc/crontab has an extra field to specify which user should run the job. So if you wanted root to run the job in /etc/crontab the above line would read:

30 00 * * * root /root/ispconfig/php/php /root/ispconfig/scripts/shell/logs.php &> /dev/null

The other things that I get messed up when using crontab: 
* file permissions not being set properly for the user to execute the job
* not specifying the entire path to the files in a script file

I'm still googling for more info ...

---

### Post by Zelut on 2005-12-12
The cron listings above were taken from crontab -e.  Is that why these don't run &/or, when I do run them manually I have to run them as sudo.  Should I edit the lines to be run as root--maybe check out the /etc/crontab?

---

### Post by barryso on 2005-12-12
Some processes just seem to only work properly when run as root.  You can run crontab commands as root using crontab -e

i.e.  

sudo crontab -e -u root

This prevents you from having to edit the /etc/crontab file.

---

### Post by barryso on 2005-12-12
Found it!

Streamripper evidently gets quite chatty to standard out.  By sending the screen output of streamripper to null the job seems to run ok from cron.

This gets added to the end of the job:

 > /dev/null 2&1 

Hope this helps someone!

---

### Post by troutbum on 2006-01-28
I'm experiencing the same problem.

Using cron to run streamripper was working well for months on Ubuntu 5.04.

When my hard drive failed, I had to migrate to a new Ubuntu 5.10 box with the same scripts and cron setup.

Some cron jobs complete normally.  Others jobs only record 4-5 minutes and quit.

If I run the script from a terminal, everything works correctly.

I tried installing mailx and I still have this problem.

I also tried appending  > /dev/null 2&1 with no success.

---

### Post by dcstar on 2006-01-28
The anacron package may be worth trying out for those having issues with the standard cron.

---

### Post by theQmaster on 2006-01-29
How secure is to let a script be ran as root  on a cron job ?

If someone gets a hand to change the php file that read like troubles to me... 
I can be wrong. What do you think ?

Q

---

### Post by athon on 2006-05-03
[QUOTE=troutbum]
I also tried appending  > /dev/null 2&1 with no success.[/QUOTE]


maybe a little late, but ro redirect stdout and stderr correctly you have to append
```
> /dev/null 2**>**&1
```

i had the same problem, and this works nice for me...

---

