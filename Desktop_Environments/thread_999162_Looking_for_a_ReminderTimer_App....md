---
title: "Looking for a Reminder/Timer App..."
date: 2008-12-01
forum: Desktop Environments
---

### Post by keithld on 2008-12-01
I'm looking for a simple app that I can type in a reminder note, set the time and have it popup and make a system sound "On Top of" any full screen application I have open... I want to use it for timing things I have in the Oven etc...

I've tried Kalarm, GNUWash & TKRemind and Kalarm seems to be the best but it doesn't popup on the top of any app I happen to be running when it goes off and the "Beep" doesn't go off...


Any ideas guys???


Thanks,

Keith

---

### Post by ajgreeny on 2008-12-01
I've been looking as well without luck so just use gnome-schedule with a task to show a png of the word "ALARM" in red which it does using eog and also sound a buzzer with gmplayer, cumbersome I know but it works and I can't find anything other than kalarm, which I'd rather not use in a gnome desktop.

The task I use in gnome-schedule is:-
export DISPLAY=:0 && eog alarm.png & export DISPLAY=:0 && gmplayer alarm.ogg

---

### Post by Rodney9 on 2008-12-01
I use Alarm Clock ([http://www.alarm-clock.54.pl](http://www.alarm-clock.54.pl)) and Festival to tell and show me my important alarms and I run my backup with Alarm Clock and grsync. 
They are downloadable with Synaptic.

---

### Post by keithld on 2008-12-02
Thanks **Rodney9**!!!!!!!

Alarm Clock Doe's exactly what I want it to do (with a bit of fiddling around, hehe), and it's loud enough to alert me of what I need to do...

---

### Post by ajgreeny on 2008-12-02
Can you actually get it to work OK?.  I've just tried it and it freezes every time I try to put in a date beyond todays in the setup alarm window.  I am trying v0.9.16-1 from getdeb which installs fine but is actually no use to me if I cant use it for dates after today's, so I've gone back to my own cron way.  Clunky, as I said, but it works.

---

### Post by keithld on 2008-12-02
> **ajgreeny said:**
> Can you actually get it to work OK?.  I've just tried it and it freezes every time I try to put in a date beyond todays in the setup alarm window.  I am trying v0.9.16-1 from getdeb which installs fine but is actually no use to me if I cant use it for dates after today's, so I've gone back to my own cron way.  Clunky, as I said, but it works.

I'm just using it as a Cooking Helper when I start some meals... I set it for the time it takes to bake potatoes or similar things so it works fine at that, I haven't tried setting it for other dates or anything like that...

I just tried creating a few alarms with different dates and times and it doesn't freeze up on me, it lists the alarms in the window list...

---

