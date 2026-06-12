---
title: "[SOLVED] cron not running a weekly job"
date: 2009-01-03
forum: General Help
---

### Post by Jose Catre-Vandis on 2009-01-03
i use xmltv to gather tv listings, and have a script written to do this. I have put the script in /etc/cron.weekly, but it never runs. I have the script permissions set to my user so I can freely run the script from a terminal with
```
/etc/cron.weekly/tv_listings
```

here is the script
```
#! /bin/sh

tv_grab_uk_rt --output=/home/jose/TVDATA.xml
tv_sort --output=/home/jose/TVDATA.xml /home/jose/TVDATA.xml
```




So why won't cron run it?

here are the contents of my crontab and anacrontab

crontab
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

anacrontab
```
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly
```

System monitor shows cron to be running and
```
 ps -ef | grep cron
root      5274     1  0 12:47 ?        00:00:00 /usr/sbin/cron
```
but no sign of anacron?

---

### Post by amauk on 2009-01-03
silly question,
but is the script executable?

---

### Post by keithweddell on 2009-01-03
I'm not sure but you may need to give full paths to tv_grab_uk_rt and tv_sort in you script.

Keith

---

### Post by dagnabit dang doohickey on 2009-01-03
Another way of doing this would be to create a user specific cron job.

Add your username to the cron.allow file:
```
sudo bash -c 'echo "*username*" >> /etc/cron.allow'
```
Edit your crontab (without sudo):
```
crontab -e
```
Add a cron job:
```
30 15 * * 0 ${HOME}/bin/tv_listings.sh
```
The above job will run ~/bin/tv_listings.sh every Sunday at 3:30 PM

```

#!/usr/bin/env bash

# tv_listings.sh

/usr/bin/tv_grab_uk_rt --output="${home}/TVDATA.xml" && \
/usr/bin/tv_sort --output="${home}/TVDATA.xml" "${home}/TVDATA.xml"

```

---

### Post by Jose Catre-Vandis on 2009-01-03
@ amauk
> silly question,
but is the script executable?

Not a silly question at all, and sorry for not stating it, yes, it is executable

@ keithweddell
> you may need to give full paths to tv_grab_uk_rt and tv_sort

I'll try that!

@ dangnabit dang doohicky  (love the nick!)

> create a user specific cron job

have already added my user in cron.allow.
preferred the easier way of simply placing the script in the cron.weekly directory, but will give this a try if adding the full paths doesn't do it for me.
"#!/bin/bash" works for all my scripts, is "#!/usr/bin/env bash" important?

once I have made changes, any way of getting cron to run the script, or do I just have to wait?

---

### Post by Jose Catre-Vandis on 2009-01-03
Hmmm, well cron doesn't seem to want to activate anything.Tried
```
crontab -e
added
1 * * * * /usr/bin/mousepad
```

and nothing happened (mousepad is my default text editor)

Also tried killing cron and starting it up again to no avail?

also saving crontab after opening up with crontab -e seems to make a file in
```
/tmp/crontab."random letters and numbers"/crontab
```
where does this end up?

also tried putting:

1 * * * * /usr/bin/mousepad

in /etc/crontab

but this didn't work either. And yes I have checked that there is an end of line return in crontab.

---

### Post by dcstar on 2009-01-03
> **Jose Catre-Vandis said:**
> Hmmm, well cron doesn't seem to want to activate anything.Tried
```
crontab -e
added
1 * * * * /usr/bin/mousepad
```

and nothing happened (mousepad is my default text editor)

Also tried killing cron and statring it up again to no avail?

If it is a graphical program then cron cannot run it (or anything) without a specific screen destination.

---

### Post by Jose Catre-Vandis on 2009-01-03
OK, well i then tried
1 * * * *  /home/jose/testcron.sh

inside testcron.sh is

#!/bin/bash
echo "cronran" > /home/jose/didcronrun.txt

made executable, this didn't run either, again worked fine from a terminal

---

### Post by dagnabit dang doohickey on 2009-01-03
```
1 * * * * env DISPLAY=:0. /usr/bin/mousepad
```
The job above will run the first minute of every hour. If you want it to run 20 minutes after the hour, it would be:
```
20 * * * * env DISPLAY=:0. /usr/bin/mousepad
```

---

### Post by dcstar on 2009-01-03
> **Jose Catre-Vandis said:**
> OK, well i then tried
**1** * * * *  /home/jose/testcron.sh
........

You do realise that you have set this to run on the 1st minute of each hour only?

If you want a GUI tool to set up your cron jobs, install the **gcrontab **package - it will appear in System-Preferences-Scheduled Tasks.

---

### Post by Jose Catre-Vandis on 2009-01-03
> **dcstar said:**
> You do realise that you have set this to run on the 1st minute of each hour only?

If you want a GUI tool to set up your cron jobs, install the **gcrontab **package - it will appear in System-Preferences-Scheduled Tasks.

Ahhh  :)

---

### Post by Jose Catre-Vandis on 2009-01-03
After some hacking around, it seems that the program tv_grab_uk_rt is the culprit and refuses to run through cron. There is no graphical output (other than in the terminal as it were) and it runs fine if I call the program from the command line. tv_sort works OK, along with any other tests I throw at cron.

tv_grab_uk_rt is owned by root and executable.

I can see tv_grab_uk_rt start up in system monitor, it manages to create the output file (empty) and then quits. No log I can find and the debug option doesn't help.

Any thoughts on where to go next?

---

### Post by Jose Catre-Vandis on 2009-01-04
Got fed up with this so wrote a little script and put it in Start Up:
```
#!/bin/bash
sleep 60
rightday=0
curday=$(date -d now +%w)
mysunday=$(date -d now +%A)

if [ "$curday" = "$rightday" ] ; then
  zenity --question --title="TV Listings" --text="It's "$mysunday", do you want to collect TV Listings?"
  itssunday=$?
else
  exit
fi

echo "Output still $itssunday"

if [ "$itssunday" = 0 ] ; then
  xfce4-terminal -x /home/jose/tv_listings.sh
else
  exit
fi
```

I have marked this thread solved, but its more of a workaround than salvation :)

---

