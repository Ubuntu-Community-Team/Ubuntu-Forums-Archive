---
title: "Script to restart server on first day of month"
date: 2009-01-10
forum: General Help
---

### Post by Warll on 2009-01-10
Does anyone know of a simple script that would restart my Ubuntu 7.10 server every month on the first day of a new month? I ask this because the gorecord program for the PX-TV402u is a bit limited. I would write it myself but I have next to no programing experience and absolutely no shell scripting experience. Thank you to anyone whom might be able to help

---

### Post by Geezopete on 2009-01-10
You could just put this in a txt file and cronjob it.


#!/bin/bash

shutdown -r now

-----------------

Then again what do you mean when you say "the gorecord program for the PX-TV402u is a bit limited" why is it limited when you ask for a simple script to restart the server?

---

### Post by blackened on 2009-01-10
For a quick explanation of crontab and how to use it see here->[http://ubuntuforums.org/showthread.php?t=102626]("http://ubuntuforums.org/showthread.php?t=102626").

---

### Post by dabang on 2009-01-10
Create a crontab file for root (will be located in /var/spool/crontab)
```
sudo crontab -e
```
with following content:

* * 1 * * /usr/sbin/shutdown -r now

This will reboot your machine on the first day of every month (I guess at midnight). See
```
man crontab
```
for details.
Please check via
```
which shutdown
```
the location of the shutdown command, could be /sbin/shutdown, I'm not quite sure now (writing this on  Windows...)

---

### Post by Warll on 2009-01-10
Ok so I wrote this:
0 0 0 1 * * /usr/sbin/shutdown -r now
to a file called crontab in /var/spool/cron/crontabs, is ther anything else I need todo?

---

### Post by blackened on 2009-01-10
> **dabang said:**
> Create a crontab file for root (will be located in /var/spool/crontab)
```
sudo crontab -e
```
with following content:

* * 1 * * /usr/sbin/shutdown -r now

This will reboot your machine on the first day of every month (I guess at midnight). See
```
man crontab
```
for details.
Please check via
```
which shutdown
```
the location of the shutdown command, could be /sbin/shutdown, I'm not quite sure now (writing this on  Windows...)

I think it would appropriately be 
```
00 00 1 * * /sbin/shutdown -r now
```

---

### Post by unutbu on 2009-01-10
According to "man crontab":

```
Each user can have their  own  crontab,
       and though these are files in /var/spool/cron/crontabs, they are not intended to
       be edited directly.
```
You should not edit /var/spool/cron/crontab files.

Instead, edit /etc/crontab:
```

#min hr    day   mon dow user command
00   00    1     *   *   root /sbin/shutdown -r now
```

---

### Post by Warll on 2009-01-10
Ok thank you that was waht I needed. Now I should have the server restarting on the first day of the month. I have just one more question though. The command I have formed to use gorecord is this:

```
gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-"%d".avi 

```

I added it to the crontab as:

```
01 00 1 * * root gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-"%d".avi 

```
My questions  are
A. How do I make the script also run if the computer has been turned off prior to the end of the month.
B. Is there some thing like the "%d" that I can add to the file name to add the date. "%d" only adds numbers 1,2,etc.

---

### Post by HermanAB on 2009-01-10
Well, I think the important question is why do you want to restart the server?  My servers typically run for about 3 years non-stop, then I either re-install (for another 3 year stint) or replace them once they are 6 years old.

Restarting every month is generally not a good idea, since someone may be running something important.

[root@gw1 html]# uptime
 14:38:48 up 369 days, 12:15,  1 user,  load average: 0.00, 0.00, 0.00
[root@gw1 html]# 

Cheers,

Herman

---

### Post by Warll on 2009-01-10
> **HermanAB said:**
> Well, I think the important question is why do you want to restart the server?  My servers typically run for about 3 years non-stop, then I either re-install (for another 3 year stint) or replace them once they are 6 years old.

Restarting every month is generally not a good idea, since someone may be running something important.

[root@gw1 html]# uptime
 14:38:48 up 369 days, 12:15,  1 user,  load average: 0.00, 0.00, 0.00
[root@gw1 html]# 

Cheers,

Herman

Yeah I thought someone would post that, don't worry this "server" is really only a P4 clocked at 2.8 with a 1TB HDD. It is hooked up the a PV-TV402U in order to save the feed from two security cameras. It also runs a network share. The network share being the only place where a restart might be a problem, if someone was write/reading a file. Of course thats not really a worry since the server will only restart at midnight, at which point in time no one should be accessing the share. 
Anyway if I were to change the crontab to:
```
* * * * * root gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-"%d".avi

```
Would that run gorecord whenever the server starts up? Or would it spawn a crippling amount of gorecord seasons?

---

### Post by unutbu on 2009-01-10
Are you sure you need to reboot? It sounds like HermanAB is right -- you don't need to reboot just to run the gorecord command.

In any case,
```

* * * * * root gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-"%d".avi

```
would spawn a crippling number of gorecord processes... one for every minute of every hour of every day... 
> 
A. How do I make the script also run if the computer has been turned off prior to the end of the month.

anacron is what you need. It is like cron, except instead of specifying an exact minute,hour,day,etc, you specify a period of time between job runs.

You don't need to edit any anacron configuration file. Anacron is set to run upon startup by default on ubuntu systems, and it looks in /etc/cron.monthly for jobs it should run once a month. So all you have to do is make a script:
```

#!/bin/bash
gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-$(date '+%Y-%m-%d_%H:%M').avi
```

Call it something like /etc/cron.monthly/do_gorecord

Make it executable:
```

sudo chmod 755 /etc/cron.monthly/do_gorecord
```

and you should be good to go.

Note that you must not give the script an extension -- no ".sh". cron and (I assume) anacron ignore all files in /etc/cron.* that have extensions.
> 
B. Is there some thing like the "%d" that I can add to the file name to add the date. "%d" only adds numbers 1,2,etc.

Yes, see the $(date '+%Y-%m-%d_%H:%M') that was added to the gorecord command.

---

### Post by Warll on 2009-01-10
Sweet! Thats perfect! The reason I was restarting the server was because gorecord will start overwriting files after its been started again. Thus I could of had a semi logical system. On the first of a month gorecord would start and would  record FILE_1 then the next day would be FILE_2 and so on till the end of the month at which point it would start over again at the beginning, thus keeping one month worth of recordings. Really one month is almost too much, these cameras are only being used since we had some nasty cases of vandalism. 

The only problem I have now though is the fact that recordings will not get overwritten. What do I had to anacron to make it delete an recordings older then one month? Oh and is it possible to make it leave a .txt file in the same directory along, I'd like to leave it there for documentation. 

Anyways thanks again, I really am starting to enjoy working with linux.

---

### Post by HermanAB on 2009-01-10
The logrotate program may be what you need.  Logrotate is used to rename log files, create fresh ones and make compressed tarballs of old ones in /var/log.  Do some reading on it:
man logrotate
less /etc/logrotate.conf

It is really easy to use.

Cheers,

Herman

---

### Post by Warll on 2009-01-10
Ok so I added that to a script file, with no .sh and restarted the server. It doesn ot seam to be recording.
Edit: As well when I run the command manually the recordings, when viewed over the network on my windows box have odd names like SS3RQV~6

Edit2:Heres the script I had added to cron.daily:
```
#!/bin/bash
gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-$(date '+%Y-%m-%d_%H:%M').avi

```

---

### Post by unutbu on 2009-01-10
```
#!/bin/bash
for file in "$( find /server/security-cam/ -type f -mtime +30 )"
do
  /bin/rm -f $file
done

gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-$(date '+%Y-%m-%d_%H:%M').avi
```

The for-loop will delete any file in /server/security-cam that is more than 30 days old.
(Age is measured with respect to the modification date).

So the script doesn't run, eh?
When you run the gorecord command from the command-line, does it perform properly?
Check that the avi file name is generated properly. 

When you put the script in /etc/cron.daily, the script should be run at 6:25am every day. 

To debug the script, you may wish to put this line in /etc/crontab:
```

*   *	   * 	 *   *	 root /etc/cron.daily/do_gorecord
```

This will run the script once every minute. You can then check that the script is being run by watching /var/log/syslog:
```

watch tail /var/log/syslog

```
This command will show you the last couple of lines in /var/log/syslog, and will refresh the display every 2 seconds. Wait for a minute. You should see an entry like this appear every time the do_gorecord script is run.
```

Jan 10 06:25:01 server /USR/SBIN/CRON[7173]: (root) CMD (/etc/cron.daily/do_gorecord)
```
Now you can tweak your script and make sure it gets run as you desire, without having to wait until 6:25am. When you succeed in getting the script to run, then you can kill all the do_gorecord processes with
```

sudo pkill do_gorecord
```

and you can delete 
```

*   *	   * 	 *   *	 root /etc/cron.daily/do_gorecord

```
from /etc/crontab.

---

### Post by Warll on 2009-01-11
Ok so I did waht you outlined in your post, except that the gorecord portiton of the script did not apear to be getting used, no files were created in the directory. So I spliced the files, left the deleting script in cron.daily and moved made a script in cron.hourly, I did adjust the recording length and chmod'd the new script. The new script does record.

Also for some reason the file names are coming up odd, even when viewed from the ubuntu box. I did a quick test and the problem is not that gorecord is stopped before its done.  

The names I'm getting:
S6DLG5~V - newest
S4ZNFQ~Z
S4ZNFQ~S
S4ZNFQ~T
SS3RQV~6

---

### Post by Warll on 2009-01-11
> **Warll said:**
> Ok so I did waht you outlined in your post, except that the gorecord portiton of the script did not apear to be getting used, no files were created in the directory. So I spliced the files, left the deleting script in cron.daily and moved made a script in cron.hourly, I did adjust the recording length and chmod'd the new script. The new script does record.

Also for some reason the file names are coming up odd, even when viewed from the ubuntu box. I did a quick test and the problem is not that gorecord is stopped before its done.  

The names I'm getting:
S6DLG5~V - newest
S4ZNFQ~Z
S4ZNFQ~S
S4ZNFQ~T
SS3RQV~6
Ok just a bit of an update, the script I have in cron.daily is not working. No files are being recorded when there should be at least two. I have the command being the only thing, plus the #bin/bash thing, in the script. The script is executable. Anyway I figured out the odd names, it messes up if I include the ":" so I replaced it with a ";", looks odd but works. Now that I think of it though, can't I just use the normal cron.tab?

---

### Post by unutbu on 2009-01-11
There are two semi-separate problems here:
[list=1]
[*] Get the script to produce the correct avi filename from the command-line. 
[*] Get the script to run via cron/anacron
[/list]
We should work on problem #1 first, because getting #2 to work on a moving target makes life a little more difficult.

If you call this test.sh
```

#!/bin/bash
NOW=$(date '+%Y-%m-%d_%H:%M')
pkill gorecord
gorecord -noaudio -input 2 -bitrate 500 -maxsize 5400 -format mpeg4 /server/security-cam/Security_cameras-"$NOW".avi

```
and make it executable, and run it as root, does it produce the right filename?

By the way, how does gorecord know when to stop? I put the "pkill gorecord" in the script so that only one recording will be made at a time.

I would stay away from filenames that use semicolons (;), because it makes writing shell scripts harder. The semicolon has special meaning for the shell -- it signals the end to a command. So if you don't protect the filenames properly in a script, the semicolon will unintentionally end a command. Colons (:) should be ok, but if I am wrong about that, I would suggest periods (.) instead of semicolons (;).> 

can't I just use the normal cron.tab?

On second thought, maybe using /etc/crontab is better than /etc/cron.daily. 
By default on Ubuntu, cron.daily runs at 6:25am every day. It sounds like for your application it would be better to run the gorecord command at 12:00am every day.
To do that, you'll need to use /etc/crontab. 

If the machine happens to be down at 12:00am, but reboots at say 12:15am, then the cron job would be missed, and gorecord would not be run. But if you edit /etc/anacrontab as well, then anacron would notice that gorecord had not been run for more than 24 hours and it would run the gorecord script at 12:15am. We can work on that later if you like.

---

### Post by Warll on 2009-01-11
1. I copied and pasted the script you gave me into a terminal. The file names were messed up. Using a period instead works though, and if you don't see a problem I'll just use it form now on. 

2. Gorecord, if run form the command line while another command line is already running it, the first command line will complain about another instance. When I had it run every minute form the cron.tab it appeared form the logs as if the kernel was killing the prior instance. 

3. It appears that the cron.hourly was sort of working over night, I have a number of files in the directory, all of them created on H:17. Except that the files themselves only have a second or two of recording in them, most are 170-180 KB with two being 68-69 KB. 

4. Since the naming seems to have been worked out I will try using the cron.tab. I'll have the record command run every hour and record for 59:50 minutes or so. I'll also schedule the delete command to run every day. I will not use any restart command.

---

### Post by unutbu on 2009-01-11
If the cronjob continues to result in short files, perhaps try
```

#min hr    day   mon dow
17   *     *     *   *    /path/to/do_gorecord 1>/dev/null 2>&1

```
This redirects stdout and stderr to /dev/null, effectively silencing all terminal output.
There was a forum thread a while ago where the user's cron job was terminating early, and for some reason silencing stdout and stderr fixed the problem.

---

### Post by dabang on 2009-01-11
> to a file called crontab in /var/spool/cron/crontabs

...no, should be /var/spool/cron/crontabs/root, as this is a cronjob for root.

---

### Post by Warll on 2009-01-18
Ok my problem seems to be that the script is not getting ran when it is in a file being called, maybe I'm calling it wrong. When I click on the script itself it opens a termaniel and it then closes right away.

---

### Post by Warll on 2009-01-25
I think I found what the issue was, my script used %, for those to work I need to do escape them: [http://www.ducea.com/2008/11/12/using-the-character-in-crontab-entries/](http://www.ducea.com/2008/11/12/using-the-character-in-crontab-entries/)

Anyway I think that should be it, thanks everyone for your help.

---

