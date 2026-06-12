---
title: "Whats wrong with this crontab?"
date: 2007-03-14
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-03-14
I cant get the btdownloadcurses or the castpodder tasks to start, 
the fisrt task is fine,
what am I doing wrong?

Steve

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly

05 00   * * 1,2,3,4,5 steve /usr/bin/btdownloadcurses /home/steve/torrents/torrent1.avi.3432902.TPB.torrent &
55 17   * * 1,2,3,4,5 steve usr/bin/killall btdownloadcurses

21 19 * * 1,2,3,4,5 steve /usr/bin/castpodder
30 19 * * 1,2,3,4,5 steve /usr/bin/killall castpodder
#

Steve

---

### Post by LotsOfPhil on 2007-03-14
How are you inputting the cron job?

Are you manually editing /etc/crontab or are you using crontab -e ?

---

### Post by mister_p_1998 on 2007-03-14
sudo gedit /etc/crontab

Steve

---

### Post by LotsOfPhil on 2007-03-14
From man crontab:
```

Crontab  is  the  program used to install, deinstall or list the tables
       used to drive the cron(8) daemon in Vixie Cron.   Each  user  can  have
       their  own  crontab,  and  though these are files in /var, they are not
       intended to be edited directly.

```

I think if you delete what you put in with gedit and put it in with crontab -e it will work.
If you need things to run as root, do sudo crontab -e

---

### Post by dannyboy79 on 2007-03-14
also, your usr/bin/killall btdownloadcurses has an incorrect path, you're forgetting the / before usr.

---

### Post by mister_p_1998 on 2007-03-14
no, tried that,
still no joy, its not even trying...
Steve

---

### Post by LotsOfPhil on 2007-03-14
get rid of "steve"

there is not supposed to be a user field in the entry. i don't know why it is in /etc/crontab

05 00 * * 1,2,3,4,5 /usr/bin/btdownloadcurses /home/steve/torrents/torrent1.avi.3432902.TPB.torrent &
55 17 * * 1,2,3,4,5 /usr/bin/killall btdownloadcurses

21 19 * * 1,2,3,4,5 /usr/bin/castpodder
30 19 * * 1,2,3,4,5 /usr/bin/killall castpodder

---

### Post by mister_p_1998 on 2007-03-14
Nope, still no good
does it take a while to update from crontab.temp?

---

### Post by dannyboy79 on 2007-03-14
don't you need to 
sudo /etc/init.d/cron restart
since  crontab is the program used to install, deinstall or list the tables
       used to drive the cron(8) daemon in Vixie Cron. based on that, I would say for your crontab to be re-referenced, you would need to restart the daemon. actually I'll correct myself, the man says you don't need to restart the daemon. just as a fyi
 i had to create a script because my wifi would for some reason disconnect once in awhile (i don't know why and was sick of troubleshooting it so I just came up with this bandade) maybe it was due to inactivity cause it was always when I came back to my machine, then I added it to sudo's crontab. it looks like this
*/5 * * * * root /usr/local/bin/.wifi &> /dev/null

and the script looks like this
#!/bin/bash
# /usr/local/bin/.wifi

PC=$(ping -c3 192.168.0.1|wc -l)

if [ $PC -ne 8 ]; then
ifdown ath0 && ifup ath0
else echo "";
fi

exit

what this does is every 5 minutes i pings my router, if the router is unreachable then it does sudo ifdown and then sudo ifup ath0 (this is my interface) if the router is reachable, than i doesn't do anything. 

why does your line have 1,2,3,4,5 in it? so what do you want your commands to do? also, you should see something within /var/log/syslog about your crontab. have you tried to add these files within /etc/cron.d/
according to man cron, they are formatted just like in your crontab file.

---

### Post by mister_p_1998 on 2007-03-15
So do I need to run the btdownloadcurses and the castpodder in a script, rather than straight in crontab? Anyidea where I should place this script?
Steve

---

### Post by LotsOfPhil on 2007-03-15
No, no need for a script. Post crontab -l (that's an L) so we can see where you're at. Also, may as well throw in cat /etc/crontab.

---

### Post by dannyboy79 on 2007-03-15
> **mister_p_1998 said:**
> So do I need to run the btdownloadcurses and the castpodder in a script, rather than straight in crontab? Anyidea where I should place this script?
Steve

no, that's not what I am saying. I was merely showing you my crontab entry for reference and explaining what the .wifi program does. i am asking what are your programs suppose to be doing. also, what does your syslog say?

---

### Post by GoCool on 2007-05-11
Not sure if this helps, but this is what I got from the man

**Bug: Although cron requies that each entry in a crontab end in a newline character, neither the crontab command or the cron deamon will detect this error. Instead, the crontab will appear to work normally. However, the command will never run. The best choice is to ensure that your crontab has a blank line at the end.**

---

### Post by dannyboy79 on 2007-05-11
should've have thought of that. This is the case for many config files within linux. I already had weird stuff happen to me when I first started linux over a year ago, it was with the fstab file needing a blank line as well. (HUH? or was it that it shouldn't have a blank line?) anyway, thanks for the tip.

---

