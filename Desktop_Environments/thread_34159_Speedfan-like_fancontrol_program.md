---
title: "Speedfan-like fancontrol program?"
date: 2005-05-13
forum: Desktop Environments
---

### Post by remmelt on 2005-05-13
Is there a fancontrol program for Ubuntu/Linux? I am looking for something like Speedfan (the Windows app).

Thanks!

---

### Post by Sam on 2005-05-13
Install lm-sensors, then get the information with the sensors command, or from a gdesklet applet or the application gkrellm.

There is an howto for lm-sensors [here](http://ubuntuforums.org/showthread.php?t=2780) and [search](http://ubuntuforums.org/search.php) for gdesklet and gkrellm.

---

### Post by remmelt on 2005-05-22
yes, i have that, and it works fine. speedfan for windows also controls the speed of the fan, so if the temperature is low, it slows the fan down a little and vice versa.

i have a 12" fan that's really OK with not going 100% all the time and it would be nice iof there were a program for that for linux... haven't seen it yet.

---

### Post by dtessier on 2005-05-24
[QUOTE=remmelt]yes, i have that, and it works fine. speedfan for windows also controls the speed of the fan, so if the temperature is low, it slows the fan down a little and vice versa.

i have a 12" fan that's really OK with not going 100% all the time and it would be nice iof there were a program for that for linux... haven't seen it yet.[/QUOTE]
There are two useful programs for this that are installed as part of lm-sensors: pwmconfig and fancontrol. pwmconfig is a script that will guide you to tweak the settings for you particular setup (how low do you want your fan to go, min and max temperatures, etc). Then, once that step is done, you just run fancontrol to control your fans using those settings. The /etc/init.d/fancontrol script can also be used to start it automatically when you start your computer.

---

### Post by deviant on 2005-05-30
when runing pwmocnfig i get this message:
"/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed"
in windows i could control fan speed by using "speedfan" software.
is there any way to persue pwmconf to detect my fans ?

---

### Post by remmelt on 2005-06-19
oh goody! i've got it working!

thanks so much!


deviant: do you have lm-sensors installed? i had to fiddle around with the fan divisor to get sensors to display fanspeeds at all. 

$ sensors
the top line will display your chip, look that one up in /etc/sensors.conf (it's a big file with lots of config that doesnt' apply to your chip!)

i set my fan divisor to 8. my chip is a w83627thf-isa-0290 on an Asus A8V motherboard, fan2 is the CPU fan, in my case. so it now says:

set fan2_div 8

than run 
$ sudo sensors -s
that reloads all the set variables in the sensors.conf
now do another 
$ sensors
and RPMs should be displayed! then you can run pwmconfig. good luck!

---

### Post by pnix on 2005-06-25
[QUOTE=deviant]when runing pwmocnfig i get this message:
"/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed"
in windows i could control fan speed by using "speedfan" software.
is there any way to persue pwmconf to detect my fans ?[/QUOTE]
My Box has the same problem. I read from somewhere that it is a bug in pwmconfig script so it can not generate fancontrol configuration file. 
What i do is create /etc/fancontrol manually like this

INTERVAL=5
FCTEMPS= 2-0290/pwm2=2-0290/temp2_input
FCFANS= 2-0290/pwm2=2-0290/fan2_input
MINTEMP= 2-0290/pwm2=25
MAXTEMP= 2-0290/pwm2=50
MINSTART= 2-0290/pwm2=120
MINSTOP= 2-0290/pwm2=85

and then 

sudo fancontrol 

if your lm-sensors config properly it should work.
note that for my mainboard fan2 and temp2 are for CPU.

---

