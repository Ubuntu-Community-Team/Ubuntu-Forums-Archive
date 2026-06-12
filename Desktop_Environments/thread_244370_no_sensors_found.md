---
title: "no sensors found ?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by kornelix on 2006-08-26
When I boot, I get a diagnostic, something like "detecting sensors  - FAILED". I started digging and found the package lm-sensors, which is already installed. I went to their website and did what they said to do. The command  $ sensors-detect  reports "No i2c device files found. Use prog/mkdev/mkdev.sh to create them". 

I cannot find this program (mkdev.sh) anywhere.

I have an Intel mainboard with the 975X chipset, including the ICH7 I/O controller. The lm-sensors web site says this chip is supported. 

Can someone point me in the right direction?

thanks

---

### Post by Anduu on 2006-08-26
Check out this how-to...

[http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors)

---

### Post by kornelix on 2006-08-26
> **Anduu said:**
> Check out this how-to...
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors)

I did see that. I is two years old and applies to a prior version of Ubuntu. Is it still valid for 6.06?  (i.e. after two years of "progress"  must one still work through elaborate obstacles to get the sensors to work?) 

I see from perusing the thread that sometimes it works, sometimes not. Seems there is plenty of room for mistakes and misunderstandings, too. 

I will give it a shot and see what happens. Wading into the muck ...

---

### Post by Anduu on 2006-08-26
> **kornelix said:**
> I did see that. I is two years old and applies to a prior version of Ubuntu. Is it still valid for 6.06?  (i.e. after two years of "progress"  must one still work through elaborate obstacles to get the sensors to work?) 

I see from perusing the thread that sometimes it works, sometimes not. Seems there is plenty of room for mistakes and misunderstandings, too. 

I will give it a shot and see what happens. Wading into the muck ...

Yes it works in Dapper...I used it...

And yes the how-to could have been done a little better...it can be a tad confusing but a little persistance pays off.

If there is an easier way to get functioning sensors I would love to try it...

---

### Post by kornelix on 2006-08-27
I got it working, and thanks for the help. I did not follow the recipe exactly, as some of it seemed irrelevant in my case (unsure about this, but the results look OK).

Here is what I did, which some others with Intel motherboards might find useful:

Getting Sensors to Work (temperatures, fan speeds, voltages)
   Ubuntu 6.06, Intel D975XBX motherboard
   (presumably any motherboard using ICH7 I/O chip)

1. Do all following steps as root user (or put sudo in front of every command)

2. Install apt package lm-sensor

3. Install and run the script mkdev.sh (purportedly in lm-sensors package, but I could not find it - following copied from this forum)
```

#!/bin/bash
NUMBER=32
OUSER=root
OGROUP=root
MODE=600
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
   echo "You do not need mkdev, system uses devfs"
   exit;
fi
fi
i=0;
while [ $i -lt $NUMBER ] ; do
   echo /dev/i2c-$i
   mknod -m $MODE /dev/i2c-$i c 89 $i || exit
   chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
   i=$[$i + 1]
done 
``` 
4. $ sensors-detect
dialog responses:
   i2c-i801: yes
   i2c-dev: yes
   NVIDIA I2C: yes
   ISA bus: no
   super I/O: no
   choose bus: smbus
   auto add to /etc/modules: yes

sensors-detect added following to /etc/modules: 
      i2c-i801
lm85
eeprom

5. $ /etc/init.d/module-init-tools

6. Add following to /etc/modprobe.d/local:
   alias char-major-89 i2c-dev
   (NOT DONE: already in /etc/modprobe.d/aliases)

7. $ update-modules

8. 
$ modprobe i2c-i801
   $ modprobe lm85
   $ modprobe eeprom

9. $ sensors
   my outputs are the following:
```
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at 4000
V1.5:       +1.48 V  (min =  +1.42 V, max =  +1.58 V)
VCore:      +1.17 V  (min =  +1.76 V, max =  +1.95 V)   ALARM
V3.3:       +3.32 V  (min =  +3.13 V, max =  +3.47 V)
V5:        +5.10 V  (min =  +4.74 V, max =  +5.26 V)
V12:      +12.19 V  (min = +11.38 V, max = +12.62 V)
CPU_Fan:    907 RPM  (min = 4000 RPM)                     ALARM
fan2:         0 RPM  (min =    0 RPM)
fan3:         0 RPM  (min =    0 RPM)
fan4:       329 RPM  (min =    0 RPM)
CPU:         +48°C  (low  =   +10°C, high =   +50°C)     ALARM
Board:       +43°C  (low  =   +10°C, high =   +35°C)     ALARM
Remote:      +40°C  (low  =   +10°C, high =   +35°C)     ALARM
CPU_PWM:    51
Fan2_PWM:   76
Fan3_PWM:   76
vid:      +1.850 V  (VRM Version 9.1)

``` 

10. Reboot

11. TBD: edit /etc/sensors.conf to correct limits. What is "PWM" ?

---

### Post by sysdemin on 2006-09-05
PWM is Pulse width modulation. Shortly described a method to make fans spin slower. Can be configured to vary according to sensed temperature with the pwmconfig script and the fancontrol demon.

---

### Post by markthecarp on 2006-09-20
Thanks kornelix, this all worked for me. Except I didn't do the reboot. My gkrellm picked up the detected sensors w/o problem so I skipped the reboot.

-mark

---

