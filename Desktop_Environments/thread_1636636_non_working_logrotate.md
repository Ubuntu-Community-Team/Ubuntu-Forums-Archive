---
title: "non working logrotate"
date: 2010-12-03
forum: Desktop Environments
---

### Post by b1235762 on 2010-12-03
i run ubuntu 10.04. my /var/log folder gone big up to 10gb.
i had ubuntu since 2 months but now logs start to go crazy. I can only delete some by Bleachbit. Logrotate give me nothing:
 [HTML]root@xxx:/home/komp# /etc/logrotate.conf
bash: /etc/logrotate.conf: Permission denied[/html]
how can I solve it?

---

### Post by tom4everitt on 2010-12-03
Try just
```

sudo logrotate -f

```

---

### Post by b1235762 on 2010-12-03
[HTML]root@xxx:/home/komp# logrotate -f
logrotate 3.7.8 - Copyright (C) 1995-2001 Red Hat, Inc.
This may be freely redistributed under the terms of the GNU Public License

U&#380;ycie: logrotate [-dfv?] [-d|--debug] [-f|--force] [-m|--mail=command]
        [-s|--state=statefile] [-v|--verbose] [-?|--help] [--usage]
        [OPTION...] <configfile>
root@xxx:/home/komp#[/HTML]

---

### Post by tom4everitt on 2010-12-03
So it says that it will need a config file as an argument. I don't really know what a config file for logrotate should look like, but I guess you could try with the one you mentioned before, which would mean
```

sudo logrotate -f /etc/logrotate.conf

```

It is strange it hasn't been cleaned automatically, it should have been. If you don't really need the logs, I would guess you could just empty the /var/log directory, but I am not sure. 


Otherwise I'm pretty lost; I mainly replied just because I saw you tried to execute a config file and hoped it would be as simple as running the command instead. 

Good luck

---

### Post by b1235762 on 2010-12-04
[html]root@xxx:/home/komp# sudo logrotate -f /etc/logrotate.conf
root@xxxp:/home/komp# /etc/logrotate.conf
bash: /etc/logrotate.conf: Permission denied
root@xxx:/home/komp#[/html]dont know what to do :(

---

### Post by tom4everitt on 2010-12-04
First of all, this part 
```

root@xxx:/home/komp# sudo logrotate -f /etc/logrotate.conf

```
worked well. In the terminal you generally only get a message if something went wrong, not if everything worked. So no message means success. If you want you can repeat this a couple of times, each time should rotate your logs one step more, successively clearing up more memory. But check /var/log and see if any memory was freed. 


The second command you executed, i.e.
```

root@xxxp:/home/komp# /etc/logrotate.conf
bash: /etc/logrotate.conf: Permission denied

```
did give you an error message. Why? Because here you are trying to execute the file /etc/logrotate.conf, which is just a config file, and therefore cannot be executed. /etc/logrotate.conf is supposed to be read by logrotate. So this command doesn't work, but neither is it supposed to.

---

### Post by b1235762 on 2010-12-04
right.
so now how can I edit logrotate so it delete all logs every day?

---

### Post by tom4everitt on 2010-12-04
There are several ways to do this. 

**Theory:**

First of all, have a look at the man page for logrotate. It is quite instructive.
```

man logrotate

```

Now, logrotate is invoked once a day by crontab. (Crontab is, as you may know, a utility for exectuting something regularly.) Have a look in /etc/cron.daily. Here should be a file called 'logrotate', which will be executed by crontab every day. The last line of this file is
```

/usr/sbin/logrotate /etc/logrotate.conf

```
which is the command that does the rotating. This is almost the command that you did earlier, the only difference being a '-f' in between.

So logrotate is most likely run every day already. But, as you can read in the logrotate man-page, logrotate will only rotate your logs when it finds it necessary. This is determined by the /etc/logrotate.conf file. It can also be forced to rotate, by the -f option.


**What to do:**

First of all, you have to determine what the problem is. Normally logrotate should be executed every day, and not letting your /var/log grow indefinitely. 

If the command you executed before, the
```

sudo logrotate -f /etc/logrotate.conf

```
worked fine, the easiet would be to edit the last line of the file /etc/cron.daily/logrotate from 
```

/usr/sbin/logrotate /etc/logrotate.conf

```
to
```

/usr/sbin/logrotate -f /etc/logrotate.conf

```
This should force logrotate to rotate the logs every day. If this doesn't work, it is probably a problem with Crontab causing your problem. Get back to me in that case, this post is growing way long as it is :)

---

### Post by tom4everitt on 2010-12-04
By the way, are you sure it is not working well on most logs, but is forgetting only one or a few that has grown huge with time? 

Tip is to use the Disk Usage Analyzer found in Applications->Accessories.

---

### Post by b1235762 on 2010-12-04
Must say it has change a bit, but I dont know exacly what (magic?)
Since yesterday it grows only to 1,4gb.
Maybe some command that will tell what is what, a diagnostic one? I would like to know what couses that logs grows such a big.
Im begginer in *unix, but in most cases I know what am I doing (in Windows i knew exacly).


my **/etc/cron.daily **looks like that:
[html]#!/bin/sh

test -x /usr/sbin/logrotate || exit 0
/usr/sbin/logrotate /etc/logrotate.conf[/html]but its read only file, how can I edit it? it have to look that:
[html]#!/bin/sh

test -x /usr/sbin/logrotate || exit 0
/usr/sbin/logrotate -f /etc/logrotate.conf[/html] ?

---

### Post by tom4everitt on 2010-12-04
Could it not be that you ran the 'logrotate -f' command that has made the /var/log smaller? 

Are you opening the file as root? It could be write protected, to set the write-flag:
```

chmod +w /etc/cron.daily/logrotate

```

then make the modifications you want. If you want, you can then unset the write-flag with:
```

chmod -w /etc/cron.daily/logrotate

```


You should be aware that you are changing the system a bit: adding the -f makes logrotate ignore it's own settings. This shouldn't be a problem as long as you don't rely on the logs being kept as long as they are supposed to, though.

---

### Post by b1235762 on 2010-12-07
yes, I run it as root. still nothing working.  Only when I execute  [html]sudo logrotate -f /etc/logrotate.conf [/html] /var/log makes smaller. Bleachbit helps too.  is logging all that stuff is really nessesery? Can I turn it off? would  it be good? I dont need to have any logs. All that logrotate *b*u*ll**sh*it** is getting me crazy.

---

### Post by tom4everitt on 2010-12-07
Okay, so sounds like there might be something wrong with your crontab then...

If you don't bother error searching, and don't care for your logs either, I would suggest putting the working logrotate command in your /etc/rc.local. All lines in the /etc/rc.local file will be executed on startup, so as long as you restart your system every now and then, this will keep rotating your logs. 

So
1. ```
sudo gedit /etc/rc.local
```
2. add ```
logrotate -f /etc/logrotate.conf
``` as the last line (sudo is not necessary here, as all commands in this file are ran as root anyway).
3. Every time you restart your system, your logs will be rotated!

---

### Post by b1235762 on 2010-12-07
my /etc/logrotate.conf: [html]
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here
[/html]can I edit it to shorter time and save just like that?:
[html]# see "man logrotate" for details
# rotate log files daily
daily

# keep 1 days worth of backlogs
rotate 1

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    daily
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    daily
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here

[/html]

---

### Post by tom4everitt on 2010-12-07
Sounds reasonable. Try it!

---

### Post by b1235762 on 2010-12-08
still nothing:( it only rotate logs when I execute [html]sudo logrotate -f /etc/logrotate.conf [/html]

---

### Post by tom4everitt on 2010-12-09
Hmm, but what if you execute 
```

sudo logrotate /etc/logrotate.conf

```
(without the -f). That works too, no? I mean, it should work once every day, because you changed to 'daily', right?

Given that, there might be causes of the error, as I see it.

1. Crontab is broken, and doesn't execute the logrotate entry, as it is supposed to. 
2. There's something wrong with the logrotate entry (the file /etc/cron.daily/logrotate). 

I would suggest creating a new logrotate entry in the /etc/cron.daily folder. It need only contain
```

#!/bin/bash
logrotate /etc/logrotate.conf

```

Be sure to make it executable also:
```

sudo chomd uga+x /etc/cron.daily/my-logrotate

```
(assuming that you named the file 'my-logrotate').

---

### Post by b1235762 on 2010-12-16
get mad and solved= re-installed the system:]

---

### Post by tom4everitt on 2010-12-17
> **b1235762 said:**
> get mad and solved= re-installed the system:]

Haha! Hate to admit it, but that's my standard solution as well :P

---

