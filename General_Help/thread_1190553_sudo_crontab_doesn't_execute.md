---
title: "sudo crontab doesn't execute"
date: 2009-06-18
forum: General Help
---

### Post by waspinator on 2009-06-18
[SOLVED]

I'm an idiot. Looks like I was doing the right thing all along but my system time was wrong. The problem was that I set the BIOS time for local time, but Ubuntu thought that BIOS was GMT, so it compensated by shifting the timezone. Lesson is always run 'date' after setting a crontab. Strange thing is, is that after updating the time in ubuntu to the proper time, it seemed to change the bios time to GMT. This isn't too much of a problem, but I set the computer to boot every day at a certain time in the BIOS, and that screwed that up. Now I just set the boot time in the BIOS with a time shift. There is probably a way to tell ubuntu that your BIOS is showing local time instead of GMT, but for now this works just fine.

If you have any problems with crontab take a look here:

[https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron](https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron)

It turns out that sudo crontab -e actually does modify roots crontab and allows you to run anything, so I wouldn't worry about mister_p_1998's suggestion (thanks), but I think it would work too.




[ORIGINAL POST]
Hi,

I'm trying to shutdown my computer everyday at 23:59.

I thought I could get this to work by using sudo's crontab.

```

sudo crontab -e

```

and then in nano (option 3) I add this

```

50 23 * * * /sbin/shutdown -h 23:59

```

but it doesn't work.

What am I doing wrong?

Thanks,

Waspinator

---

### Post by Hund on 2009-06-18
You could try to add this as a cronjob as root:

> 59 23 * * * /sbin/shutdown -h now

---

### Post by dcstar on 2009-06-18
> **waspinator said:**
> Hi,

I'm trying to shutdown my computer everyday at 23:59.

I thought I could get this to work by using sudo's crontab.

```

sudo crontab -e

```

and then in nano (option 3) I add this

```

50 23 * * * /sbin/shutdown -h 23:59

```

but it doesn't work.

What am I doing wrong?

Thanks,

Waspinator

Try this (case is also important):

```
50 23 * * * /sbin/shutdown -H 23:59 &
```

---

### Post by mister_p_1998 on 2009-06-18
youre doing it all wrong mate,
the way I do it is:
sudo gedit /etc/crontab

the command after the time/date is: root /usr/sbin/shutdown -h now 
(note the space after root)

you need to do it this way for all programs that do stuff to the system (eg shutdown) crontab - only runs programs as YOUR user (you) a user cant shutdown the system without the admin password, root can.

Steve

---

### Post by waspinator on 2009-06-18
> **mister_p_1998 said:**
> youre doing it all wrong mate,
the way I do it is:
sudo gedit /etc/crontab

the command after the time/date is: root /usr/sbin/shutdown -h now 
(note the space after root)

you need to do it this way for all programs that do stuff to the system (eg shutdown) crontab - only runs programs as YOUR user (you) a user cant shutdown the system without the admin password, root can.

Steve

Thanks, I'll try that.

But why does ubuntu have 2 crontabs for root? 

I'm probably really confused. I always that that sudo and root were the same guy (that sudo just pointed to root). And that when I type "sudo crontab -e" I'm actually editing roots crontab. sudo can shutdown the server fine btw. 

And I know that sudo crontab -e does not edit my users crontab because typing JUST crontab -e displays a different crontab.

So my question I guess is what's sudo crontab -e for if I have to edit /etc/crontab for root stuff anyway?

Thanks,

Waspinator

---

### Post by mister_p_1998 on 2009-06-19
> **waspinator said:**
> Thanks, I'll try that.

But why does ubuntu have 2 crontabs for root? 

I'm probably really confused. I always that that sudo and root were the same guy (that sudo just pointed to root). And that when I type "sudo crontab -e" I'm actually editing roots crontab. sudo can shutdown the server fine btw. 

And I know that sudo crontab -e does not edit my users crontab because typing JUST crontab -e displays a different crontab.

So my question I guess is what's sudo crontab -e for if I have to edit /etc/crontab for root stuff anyway?

Thanks,

Waspinator


I think sudo crontab -e edits your own crontab as root, but still only YOUR crontab, you could only do crontab -e for root if you were logged on as root, which you normally cant do. Sudo gedit /etc/crontab edits the file owned by root using sudo, the file in /etc isnt normally write accessible by you.

Its because root has to do cron jobs that may effect ALL users, your cron runs programs ONLY for you, think of it as if you are logging onto a server, there are many more users than just you, Linux runs kinda like that.

Steve

---

### Post by waspinator on 2009-06-23
Thanks for your help mister_p_1998. Turned out I was doing the right thing, but my time was set a few hours back. After running a root command every minute and seeing that it worked, I had no idea why it wouldn't shutdown when I told it too. For some reason it took me that long to check my system time.

Oh well, I guess you live and learn.

Thanks,

Waspinator

---

