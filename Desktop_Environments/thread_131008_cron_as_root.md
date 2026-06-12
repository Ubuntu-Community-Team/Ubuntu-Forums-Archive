---
title: "cron as root"
date: 2006-02-15
forum: Desktop Environments
---

### Post by spudse on 2006-02-15
I have a bash script that I would like to run as a cronjob.

The bash script needs to be run as root, because it executes tethereal that needs root. The script runs fine when I run it like this "sudo script.sh". But when I add the following line to /etc/crontab nothing seems to happen:

0,5,10,15,20,25,30,35,40,45,50,55 * * * * root /home/myusername/script.sh

When I edit script.sh to do something that doesn't need root it runs fine.

So the script is correct and the crontab schedules right aswell. But it doesn't run as root. How can I fix this?

Thanks.

---

### Post by dcstar on 2006-02-15
[QUOTE=spudse]I have a bash script that I would like to run as a cronjob.

The bash script needs to be run as root, because it executes tethereal that needs root. The script runs fine when I run it like this "sudo script.sh". But when I add the following line to /etc/crontab nothing seems to happen:

0,5,10,15,20,25,30,35,40,45,50,55 * * * * root /home/myusername/script.sh

When I edit script.sh to do something that doesn't need root it runs fine.

So the script is correct and the crontab schedules right aswell. But it doesn't run as root. How can I fix this?

Thanks.[/QUOTE]
sudo crontab -e

---

### Post by spudse on 2006-02-15
Edit: I still doesn't work :(

Thanks dcstar,

I did it and within a few minutes I will see whether it worked. But in which file can I see which cronjob I set with "sudo crontab -e" ?

---

### Post by spudse on 2006-02-16
I just found out something weird.

When I do

$sudo su
$crontab -e

there is two lines:
0,5,10,15,20,25,30,35,40,45,50,55 * * * * tcpdump -w /home/user/test.txt
0,5,10,15,20,25,30,35,40,45,50,55 * * * * touch /home/user/test2.txt

The first line simply doesnt execute (secondline does execute). Why is that?

---

### Post by dcstar on 2006-02-16
[QUOTE=spudse]I just found out something weird.

When I do

$sudo su
$crontab -e

there is two lines:
0,5,10,15,20,25,30,35,40,45,50,55 * * * * tcpdump -w /home/user/test.txt
0,5,10,15,20,25,30,35,40,45,50,55 * * * * touch /home/user/test2.txt

The first line simply doesnt execute (secondline does execute). Why is that?[/QUOTE]
On my system tcpdump is in /usr/sbin, touch is in /usr/bin.

You should **always** use the full path and not assume that cron uses the same shell you use manually - it doesn't.

---

### Post by spudse on 2006-02-16
Thanks dcstar, it did get me some further. But still it doesn't work. I will post the full script and crontab -e here:

/home/user/script.sh
```
#!/bin/bash

killall tcpdump
var=$(date +%G%m%d-%k%M)
/usr/sbin/tcpdump -w /home/user/$var.txt
```

sudo crontab -e
```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /home/user/script.sh
```

When I simply put */usr/sbin/tcpdump -w /home/user/log.txt* instead of *script.sh* in the crontab it runs. When I do *sudo script.sh* it also runs. Just the combination that doesnt do anything at all.

---

### Post by spudse on 2006-02-17
Well I think I got it all working now. 

There is only one problem, which is that (all) my crontab dont run between 00:00 and 08:00. Why is that?

---

