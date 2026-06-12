---
title: "Battery problems with 8.04"
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FranciscoLopez on 2008-05-21
[LEFT][/LEFT]ok i'm using 8.04 in an inspiron 9400 everything works fine except the battery,  first  ,it reports a different discharge time and rate when you run the acpi command than  what is shown automatically, second it sucks my battery time, in winxp I had like 1:45 in Ubuntu i get 1:05.

third my battery's total capacity has gone down from  69%  to 54% in 2 DAYS!!!!!!![LEFT][/LEFT]

---

### Post by mtbsoft on 2008-05-21
How old is the battery?  Could be a fault in the battery itelf or just that it's getting to the end of its life.  I've the same laptop, with a 9 cell battery and I'm finding the Hardy battery life to be comparible with Gutsy (between 2.5 and 3 hrs), which was similar to XP.  What software are you running?

---

### Post by drfarrin on 2008-05-22
I'm having a similar issue, I got a massive battery for my 9300 (just the previous year's model) and if I have the right settings on xp, it can last up to 4 hours, now it lasts barely 1:30.

---

### Post by cooldudeny on 2008-05-22
i think i am having the battery issue it is draining at the speed of light i always thought linux is suppose to be better but it is turning out to be a pain so i guess i will be going back to windows .... atleast i can work the issues a little better in windows but i have been using it for ages now

---

### Post by FranciscoLopez on 2008-05-22
it's practically new!
its my first replacement battery, the original that came with the equipment lasted 14 months, this one is less than 3 months old.
and running practically just netbeans, mysql community server and firefox.

---

### Post by FranciscoLopez on 2008-05-22
here is more info:

[B][U]Charging
[/U][/B]

~$ acpi
     Battery 1: charging, 2%, 02:10:06 until charged

acpi -V
     Battery 1: charging, 3%, 02:50:34 until charged
     Thermal 1: ok, 48.0 degrees C
  AC Adapter 1: on-line

$ cat /proc/acpi/battery/BAT0/*
alarm:                   720 mAh
present:                 yes
design capacity:         7200 mAh
last full capacity:      3616 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL 00
serial number:           683
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1185 mA
remaining capacity:      128 mAh
present voltage:         12780 mV

$ acpi -ba
     Battery 1: charging, 4%, 03:22:26 until charged
  AC Adapter 1: on-line

**_unplugged_**:
 acpi
     Battery 1: discharging, 100%, 02:22:11 remaining

 acpi -V
     Battery 1: discharging, 100%, 02:22:11 remaining
     Thermal 1: ok, 47.0 degrees C
  AC Adapter 1: off-line


cat /proc/acpi/battery/BAT0/*
alarm:                   720 mAh
present:                 yes
design capacity:         7200 mAh
last full capacity:      3616 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL 00
serial number:           683
battery type:            LION
OEM info:                Sony
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            3038 mA
remaining capacity:      7200 mAh
present voltage:         12249 mV

acpi -ba
     Battery 1: discharging, 91%, 3313:00:00 remaining
  AC Adapter 1: off-line


now i sense my bat is already toast 
here are 2 images taken aprox 8 minutes apart from my laptop
in those 8 mins the bat went from 90%+ to 0%

before :

[IMG][[IMG]http://img80.imageshack.us/img80/711/pantallazosk2.th.png[/IMG]](http://img80.imageshack.us/my.php?image=pantallazosk2.png)[/IMG]

after:

[IMG][[IMG]http://img139.imageshack.us/img139/7410/pantallazo1hr0.th.png[/IMG]](http://img139.imageshack.us/my.php?image=pantallazo1hr0.png)[/IMG]

---

### Post by Melindrea on 2008-06-16
I'll add my issues to this. I haven't tried using it without power for too long, but the battery time is 1 hour on Ubuntu and 2 hours on Windows. Laptop is not even six months old, so the battery isn't that old either (got it at Christmas).

---

### Post by sdennie on 2008-06-16
It could simply be that you have a faulty battery.  I've not noticed anything in Ubuntu that specifically would shorten the lifespan of a battery.  My XPS m1330 has a 9 cell battery and it's maximum capacity is decreasing at a rate well below 1% per month.

---

### Post by fragos on 2008-06-16
Install the powertop package. It will help you find the largest power consumers and configuration suggestions to extend battery life. My 1420n gets almost 5 hours with the 9 cell battery. I saw little or no differences in power consumption between 7.04, 7.10 and 8.04. You might also check the Power Management Preferences which are a major factor in battery life.

---

