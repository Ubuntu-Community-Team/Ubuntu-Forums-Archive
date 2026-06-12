---
title: "how to run a script every OTHER saturday"
date: 2010-05-28
forum: Desktop Environments
---

### Post by Paper Pusher on 2010-05-28
i'm running unbr 9.10.
i want to run a script every other saturday at midnight. it needs sudo.

i've studied gnome schedule 2.1 and i'm utterly confused.

help!

---

### Post by lykeion on 2010-05-28
Check this:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Paper Pusher on 2010-05-28
thanks.  i'll test weekday 6/2 in the morning.

is there any documentation of the advanced edit dialog?
i'm thinking especially of the in a step width option.

[comment: google calendar is infinitely easier to use for this sort of thing]

---

### Post by iponeverything on 2010-05-28
If it's a bash script you can put it in /etc/crontab to run every week and then add this code to the top of the script so that it only runs on odd numbered days.. 

```

day=`date +%d`

if [ $((day % 2)) -eq 0 ]; then
exit
fi

```

I can see now though, how it gets messed up..

---

### Post by Paper Pusher on 2010-05-29
i want to thank everyone who posted.

here is the current state of my research:
[LIST]
[*]cron is typical *nix.  you can do anything if you can figure it out.
[*]gnome schedule is obtuse and poorly documented.  I found no documentation of the advanced options.
[*]kalarm was refreshingly different.  i can set a start date and repeat my script every 14 days.
[/LIST]

i am new to ubuntu and totally indifferent to kde vs. gnome.  i standardized on ubuntu because it seemed to be the main *buntu.
but i am using okular because it has more of the features i want.  kalarm is the same.

---

