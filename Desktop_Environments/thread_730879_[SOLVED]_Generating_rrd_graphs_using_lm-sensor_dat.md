---
title: "[SOLVED] Generating rrd graphs using lm-sensor data"
date: 2008-03-21
forum: Desktop Environments
---

### Post by chapterthree on 2008-03-21
Hi All,

I would like to start graphing my system sensor information (Temps, Fan RPMs, HDD temps, etc).  I have installed hddtemp and lm-sensors and have both working perfectly (data being displayed correctly by sensors-applet).

I'm having an issue getting sensord to work, which looks like the perfect solution for graphing sensor data.  First question is, is sensord the right tool, and if not, which is a better solution?

I can start posting my sensor configuration data if sensord is the correct tool to use to figure out why sensord won't start (errors out on not being able to read a sensor component):

```
Mar 21 08:17:56 home sensord: Error getting sensor data: w83627thf/#6: Can't access procfs/sysfs file
Mar 21 08:17:56 home sensord: sensord failed
```

I have even gone so far as to comment out everything (relevant to my chip) in /etc/sensors.conf, but I still get the same error.

---

### Post by chapterthree on 2008-03-22
After enough searching I found what seems to be a better solution: collectd-sensors (and a handful of other collectd plugins).

---

