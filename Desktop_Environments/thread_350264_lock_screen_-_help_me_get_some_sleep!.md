---
title: "lock screen - help me get some sleep!"
date: 2007-01-31
forum: Desktop Environments
---

### Post by munkar on 2007-01-31
i have a bad habit of messing around on my laptop before i go to sleep, causing me to procrastinate about actually hitting the sack. so, i've made GNOME lock my screen using cron at midnight (gnome-screensaver-command --lock). simple enough.

but i'd really like to have a better solution. it's too easy for me to just groan when the lock screen dialogue comes up, and to enter my password. is there any way to me to specify a different, longer password, just for this specific daily instance of lock screen? i have some idea of how it could theoretically be done, but i wonder specifically

1) is it possible to set a different password for lock screen from the one i use to login as root, and
2) if so, is it possible to set that password from the command line?

thanks!

---

### Post by munkar on 2007-02-01
and ... it's 2am and cron didn't run lock screen properly.

this is my crontab entry...what's going on?

55 1 * * * export DISPLAY=:0 && /usr/bin/gnome-screensaver-command --lock

---

### Post by munkar on 2007-02-08
still wondering about this. it would be a big help!

---

### Post by shareMenaPeace on 2007-02-08
DOnt knwo for the password but for locking this cna be done in System -> Preferences -> Screensaver

---

### Post by munkar on 2007-02-08
that much i know, but the question is why cron doesn't run "gnome-screensaver-command --lock" (or "gnome-session-save --kill", i've discovered).

wait...i just downloaded xlock from synaptic and it seems to do just what i want....!

---

### Post by mithras86 on 2007-02-11
I dont no much about cron, but it's not possible to set up another -second- password just for the lock screen. Or you have to code a programme for yourself which will do the same as locking your screen.
So: what about  a cron with just the command 'poweroff' ;)

---

### Post by munkar on 2007-02-11
thanks for the idea, Mithras, but the problem with making my computer shutdown is that it has some tasks to perform in the morning (downloads podcasts and plays one as an alarm depending on the day of the week).

what i've done is to simply use xlock. i added the following line to my crontab file, and i'm happy with it:

```
0,5,10,15,20,25,30,35,40,45,50,55 0 * * * export DISPLAY=:0 && xlock -mode blank # lock screen at 12:00am and every 5 mins afterward
```

as you can see, i gave up on the custom password idea and decided to just make it keep locking on me every five minutes so that i would get tired of unlocking it again and again.

---

