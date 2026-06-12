---
title: "fancontrol doesn't work after reboot"
date: 2009-05-07
forum: General Help
---

### Post by whitethorn on 2009-05-07
Hi,

I have a new computer, with a very loud case fan.  I want to regulate it using pwmconfig/fancontrol.  So far whenever I run 

```
pwmconfig
```

Let's me setup my fans. I then run ```
sudo fancontrol
``` everything works fine.  

After I restart my computer, and I start fancontrol

> sudo fancontrol 
Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=10

Settings for hwmon4/device/pwm1:
  Depends on hwmon0/device/temp1_input
  Controls hwmon4/device/fan1_input
  MINTEMP=45
  MAXTEMP=60
  MINSTART=255
  MINSTOP=60
  MINPWM=60
  MAXPWM=255

Enabling PWM on fans...
Starting automatic fan control...


Unfortunately it doesn't do anything. Ideas?

---

### Post by whitethorn on 2009-08-27
I got this to work by just playing around and testing the different pwm_enable

I had to add these two commands to /etc/rc.local

```

echo 1 > /sys/class/hwmon/hwmon4/device/pwm4_enable
/usr/local/sbin/fancontrol /etc/fancontrol &

```

The actual fan is pwm1, but only enabling it didn't do anything, wierd though.

---

