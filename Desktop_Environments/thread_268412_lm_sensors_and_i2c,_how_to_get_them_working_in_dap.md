---
title: "lm_sensors and i2c, how to get them working in dapper"
date: 2006-09-30
forum: Desktop Environments
---

### Post by daedalusman on 2006-09-30
So I installed the lm_sensors package and tried the "sensors-detect" command but it gave me this error...

```
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
```

I have the i686-smp kernel installed, is this the problem, does it not have support for i2c built into it or is there something else that I'm missing here? Can someone please help me out here, its one of the few things I haven't been able to get to work in dapper. I had this working in breezey but ever since updating to dapper I have to unable to achive this functionality. Thanks for any help.

---

### Post by danielph on 2006-09-30
I have this working in dapper ok, on 386 kernel, but not sure that is your problem.

Have you got libsensors installed?

---

### Post by daedalusman on 2006-09-30
Yeah, I actually just came across this article
[http://ubuntuguide.org/wiki/Dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)
and that got things going for me. Now I just need to figure out how to configure conky to use them. Thanks.

---

