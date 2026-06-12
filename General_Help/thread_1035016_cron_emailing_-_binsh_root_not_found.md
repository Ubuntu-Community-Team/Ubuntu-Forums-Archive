---
title: "cron emailing - /bin/sh: root: not found"
date: 2009-01-09
forum: General Help
---

### Post by lift28 on 2009-01-09
cron is running fine but, i can not  seem to find a reason for the emails-- they all say the same 
/bin/sh: root: not found
sh is link to:
/bin/sh -> dash
this is happing on my other box also- has for yrs lol just tired of it 
thanks in advanced

---

### Post by unutbu on 2009-01-09
If you type```

/bin/sh -c root
```

You will get the error message:
```

/bin/sh: root: not found
```
This looks similar to the message you are receiving in the email.

This leads me to believe that you have a crontab entry which is asking cron to run a program named "root". 

How about type```


crontab -e

```
and look for a line that begins with the word "root" in the 6th column
```

*   * 	   * 	 *   *   root

```
Note that /etc/crontab uses a different format than personal crontabs.
In /etc/crontab, the 6th column specifies the user who is supposed to run the command,
while in a personal crontab the 6th column specifies the command.

If this does not help, type
```

sudo -i
crontab -e
```

and look at root's personal crontab.

If that does not help, match the timestamp on the email against the timestamps in /var/log/syslog to find the full crontab command that is generating the error message.

---

### Post by lift28 on 2009-01-09
thanks for your response
my crontab looks as you said

cheri@cheri:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

20 2    * * *   root    /etc/network/if-up.d/ntpdate >/dev/null 2>&1
47 3    * * 7   cheri   /etc/backup-jobs/cheri-weekly-backup


the relating line to the email is:

/USR/SBIN/CRON[3039]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

i check all users crontabs - they are all empty-- the only changes are the last 2 lines i made

---

### Post by unutbu on 2009-01-09
Look inside /etc/cron.hourly. One of the scripts in that directory may be causing the problem.

Edit: Although I don't think this is the source of your current problem, note that cron has a funny quirk/bug which requires that each entry in the crontab must end with a newline character.
This is the reason that there is an empty comment line after the last regular crontab entry.

```
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

You may wish to move 
```

20 2 * * * root /etc/network/if-up.d/ntpdate >/dev/null 2>&1
47 3 * * 7 cheri /etc/backup-jobs/cheri-weekly-backup
```
up above the empty comment line to take advantage of its purpose.

(See the BUGS section of "man crontab" for info on the funny newline character bug).

---

### Post by lift28 on 2009-01-09
well i remove the empty line and put the # at the end of the file,
then sudo crontab /etc/crontab.
still no luck
any other ideas?
thanks for your help

---

### Post by lift28 on 2009-01-12
bummmp

---

### Post by lift28 on 2009-01-15
damn dump again

---

### Post by lift28 on 2010-10-25
this begins happening from running sudo crontab /etc/crontab, it then makes a cron file for root in /var/spool/cron/crontabs.
run rm /var/spool/cron/crontabs/root and it is fixed.

---

