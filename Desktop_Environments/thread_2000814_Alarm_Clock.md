---
title: "Alarm Clock"
date: 2012-06-10
forum: Desktop Environments
---

### Post by ajpearson on 2012-06-10
I have been trying to get an alarm clock application that plays audio. For some reason Kalarm cannot do it - not yet worked out why?

I am now looking at Alarm Clock and it does play the audio file ok. However, and I am sure this is possible, I cannot see how I can set a date in the future - it only allows today.

I cannot see any preferences to help me & there appears to be no user guidance anywhere?

Thanks

Andrew

---

### Post by Frogs Hair on 2012-06-10
Take Look at Wakeup in the software center. It can play music and start the computer. I have not used it but it seems to be closer to what you are looking for.

---

### Post by SpeedyGonsales on 2012-06-10
In repo for 1204 is alarm clock 1.2.5 with URL of its author [www.alarm-clock.pl](www.alarm-clock.pl)

It has 4 options:

1.today
2.tomorrow
3.single day (whatever day in future, you choose it using calendar control)
4.schedule

I dowloaded a while ago alarm clock 0.3.1 (not from repo), URL of its author is alarm-clock.pseudoberries.com

It has only today and schedule, but with schedule you can get 7 days ahead, and that is enough for most of us.
Both these apps can play sound or start app of your choosing, simplest solution is to install alarm clock from repo, as it has everything you need.

---

### Post by ajpearson on 2012-06-10
I wanted something that worked all year - so I will go back to Kalarm and see if I can make more sense of it.

Thanks for all your help.

---

### Post by Rodney9 on 2012-06-10
sudo rtcwake -m mem -t `date +%s -d"2011-01-11 07:30"`

sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`


[http://bytebaker.com/2009/08/23/roll-your-own-linux-alarm-clock/](http://bytebaker.com/2009/08/23/roll-your-own-linux-alarm-clock/)

++++++++++++++++++++++++++++++++++++++++++++


I use a script called alarm.sh

```
#!/bin/sh

ogg123 -z ~/Music/*.ogg
```

and added it to cron

```
33 04 * * * /bin/alarm.sh 
```

and this 

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

rtcwake wakes my laptop from sleep at 4:30am
cron plays my alarm.sh script at 4:33am
ogg123 -z shuffles my Music directory.


Rodney

---

