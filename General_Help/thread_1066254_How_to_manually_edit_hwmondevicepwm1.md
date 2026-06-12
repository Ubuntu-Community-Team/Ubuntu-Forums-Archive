---
title: "How to manually edit hwmon/device/pwm1?"
date: 2009-02-10
forum: General Help
---

### Post by Antioch on 2009-02-10
I would like to manually control the pwm that drives my chasis fans.

I've installed lm-sensors, used pwmcontrol to find and test my devices. I now know that my fans are controlled my hwmon0/devices/pwm4. According to the guide here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org") I can make a script that will switch the speed depending on the temperature.

I would like to be able to manually echo integer values to hwmon0/devices/pwm4 so that I can control the speed on my own.

(Really what I would like to do it set the fans to one speed and leave them that way - but before then I'd like to test what speed is best)

So, how can I edit this device?

Thanks.

---

