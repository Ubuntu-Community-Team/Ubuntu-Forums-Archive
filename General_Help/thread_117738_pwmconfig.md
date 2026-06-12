---
title: "pwmconfig"
date: 2006-01-15
forum: General Help
---

### Post by phidippus on 2006-01-15
I like to use pwmconfig to control the cpu fan activity, but I get

[COLOR="DarkGreen"]pwmconfig[/COLOR]
[COLOR="Red"]/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)[/COLOR]

I also get

[COLOR="DarkGreen"]sensors-detect[/COLOR]
 [COLOR="Red"]Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.[/COLOR]

But I have been able to monitor the cpu temp by using ksensors. I really want to use pwmconfig. What should I do?

---

