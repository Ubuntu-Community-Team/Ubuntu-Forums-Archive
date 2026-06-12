---
title: "speedfan linux port"
date: 2006-08-06
forum: Desktop Environments
---

### Post by jgoyvaer on 2006-08-06
Hi,

Does somebody in here knows whether there's a linux equivalent of the speedfan windows utility ? Something straightforward to link the temperature with the fan rpms ?

I'm trying to cut the fan noise on my older pentiumIV 1.4ghz but only with speedfan under windows I manage that... Tried a lot of echo's to /proc/acpi/... files but that doesn't work at all.

Thanks for any clue !

Jan

---

### Post by Grard on 2006-08-06
'fancontrol' will do that for you.

It's in the package 'lm-sensors' and you set it up with 'pwmconfig'

---

### Post by jgoyvaer on 2006-08-06
:D yes ! I did the trick. Having lm-sensors work was the hard part. 

incredible this silence !!! :-)

THANKS A LOT !

---

### Post by wareagle on 2007-12-31
I have a Dell Latitude D600 and when I run sensors-detect, it says no sensors were found.

I desperately need fan control because my computer overheats.  (I've tried cleaning it out and putting new thermal grease on it but nothing works.

:(

---

### Post by Mr Fredrick on 2007-12-31
I have the same problem with my Dell Latitude, the fan turns on, mostly on low, and stays on for long periods but the unit still feels too hot.

Here is what I get if I run pwmconfig:

me@me-laptop:~$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)

Do I need to install/configure anything else to get this to work?

---

### Post by wareagle on 2008-01-02
After a few minutes to a few hours, my ethernet goes out.  (I can fix it by running my fans full blast in Windows.)

Do you ever have similar problems?

---

### Post by sicofante on 2008-03-10
Any GUI for fancontrol?

---

### Post by zuknivek on 2008-03-27
I finally decided to make the switch to ubuntu with my main computer after having it for nearly a year on my laptop. Now that i have ubuntu 7.10 going i cant seem to get lm sensors to work. When i was using xp i had speedfan working fine and my computer is homemade so i know it has sensors and stuff.

---

### Post by Sealbhach on 2008-05-23
I get the same problem after installing lm-sensors. 

```
/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)
oliver@oliver-vaio:~$ modprobe sensor modules
FATAL: Module sensor not found.
oliver@oliver-vaio:~$ 

```

What do do we do now?

> **Mr Fredrick said:**
> 

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)

Do I need to install/configure anything else to get this to work?

---

### Post by skada on 2008-06-03
Please visit this site for detailed configuration og sensors and fancontrol 
Its quite lengthy. Have fun ! :)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)



My first post !!

---

### Post by JuBeZ on 2008-07-23
I did the pwmconfig and it seems like my fans have stopped or slowed because my computer is much quieter and running significantly hotter. Can someone please point me in the right direction? It's a Dell XPS 1530

---

