---
title: "HELP!! All my hd space is gone!"
date: 2009-01-28
forum: Desktop Environments
---

### Post by lady_jade on 2009-01-28
HI everyone. I noticed that all my space on my hard drive just disappeared for some unknown reason to me. I have a 40g hd, and my average free space is normally between 14.5g. How some time ago I noticed that my hd space reached 9g free. then today its all gone. I haven't fool around the system, and I don't install a lot of things. 
So please can someone tell what went wrong or whats wrong? is it a virus(which would be weird) or some internal error?:(

---

### Post by caljohnsmith on 2009-01-28
Can you still boot into your Ubuntu install? If so, how about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
df -h
```
And we can work from there if you want.

---

### Post by ken_r on 2009-01-29
Sometimes log files can grow very large if there is an error condition. You might want to search for files larger than 1GB to see if that is the problem.

---

### Post by taurus on 2009-01-29
And if you have a backup program running (from cron), it will make a backup of your system and will dump it to /var/backups, taking up a lot of space.

---

### Post by lady_jade on 2009-01-29
> **caljohnsmith said:**
> Can you still boot into your Ubuntu install? If so, how about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
df -h
```
And we can work from there if you want.

> **taurus said:**
> And if you have a backup program running (from cron), it will make a backup of your system and will dump it to /var/backups, taking up a lot of space.

> **ken_r said:**
> Sometimes log files can grow very large if there is an error condition. You might want to search for files larger than 1GB to see if that is the problem.

[I][B]Well I am unable to log in. I just got my ubuntu cd in the mail so I am going to back up and then format. 
Before I couldn't log in I just noticed the space disappearing. 
Also I didn't have any backup program unless ubuntu has one that I don't know about. 
Can anyone tell me how to avoid something like this happening again to me please? I would greatly appreciate it. 

[/B][/I]

---

