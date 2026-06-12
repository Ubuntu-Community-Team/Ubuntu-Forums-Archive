---
title: "Performance Issues"
date: 2009-05-24
forum: General Help
---

### Post by WeaponsTheyFear on 2009-05-24
Hello guys,
I am running the latest version of Ubuntu on a 64bit AMD.  I have been noticing that my CPU usage is usually kinda high, usually between 7 and 14 % and if I do something it will shoot up.  Thought this was kind of odd since XP only sat around 3 and 4 %.

I am on an EMachines W3400, AMD 64 2ghz with 1gig Kingston RAM.  I have an NVidia card installed, with 128 MB,  Also have a soundblaster live 24 bit sound card.

I'm not a very experienced linux user, but figured there has to be something causing this.  I notice in System Monitors process list there is well over 30 items there.  The load average tells me ...

0.14    0.44   0.45

These stats are from no programs opened.  Throughout the day, I will have Apachefriends LAMP stack running, Geany text editor, Firefox and some Rythm Box music player going, and the performance doesn't seem to do much worse than the system sitting doing nothing.

So, any performance tips or help for me ?

---

### Post by DeMus on 2009-05-24
> **WeaponsTheyFear said:**
> Hello guys,
I am running the latest version of Ubuntu on a 64bit AMD.  I have been noticing that my CPU usage is usually kinda high, usually between 7 and 14 % and if I do something it will shoot up.  Thought this was kind of odd since XP only sat around 3 and 4 %.

I am on an EMachines W3400, AMD 64 2ghz with 1gig Kingston RAM.  I have an NVidia card installed, with 128 MB,  Also have a soundblaster live 24 bit sound card.

I'm not a very experienced linux user, but figured there has to be something causing this.  I notice in System Monitors process list there is well over 30 items there.  The load average tells me ...

0.14    0.44   0.45

These stats are from no programs opened.  Throughout the day, I will have Apachefriends LAMP stack running, Geany text editor, Firefox and some Rythm Box music player going, and the performance doesn't seem to do much worse than the system sitting doing nothing.

So, any performance tips or help for me ?

The numbers you wrote down indicate the load averages in 1, 5 and 15 minutes, I presume?
Well, mine are 4.76, 4.32 and 4.22
This is strange since my system (quad core machine) is running 100% on each core 24/7. It also says that in the list below these values.
So, I have no idea what these numbers mean.

---

### Post by Legace on 2009-05-24
The Ubuntu System Monitor is pretty heavy.
Try opening Terminal, and typing **top**
Look at the %CPU column. The numbers should add up to 4-5%

---

### Post by alphacrucis2 on 2009-05-24
> **WeaponsTheyFear said:**
> Hello guys,
I am running the latest version of Ubuntu on a 64bit AMD.  I have been noticing that my CPU usage is usually kinda high, usually between 7 and 14 % and if I do something it will shoot up.  Thought this was kind of odd since XP only sat around 3 and 4 %.

I am on an EMachines W3400, AMD 64 2ghz with 1gig Kingston RAM.  I have an NVidia card installed, with 128 MB,  Also have a soundblaster live 24 bit sound card.

I'm not a very experienced linux user, but figured there has to be something causing this.  I notice in System Monitors process list there is well over 30 items there.  The load average tells me ...

0.14    0.44   0.45

These stats are from no programs opened.  Throughout the day, I will have Apachefriends LAMP stack running, Geany text editor, Firefox and some Rythm Box music player going, and the performance doesn't seem to do much worse than the system sitting doing nothing.

So, any performance tips or help for me ?

Can you see what process is using the cpu. You can run the system monitor to see but that program itself uses a bit of cpu. Other option is to use the top (or htop if you install it from the command line) as these use less cpu themselves.

---

