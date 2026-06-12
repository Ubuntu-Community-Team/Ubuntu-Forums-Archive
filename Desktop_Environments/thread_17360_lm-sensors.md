---
title: "lm-sensors"
date: 2005-02-28
forum: Desktop Environments
---

### Post by kiwigander on 2005-02-28
I'd like to try lm-sensors on my Warty 4.10 system.  I used synaptic to install version 2.8.7-1warty1, followed the instructions to mount sysfs (which was already mounted) and modprobe i2c_sensor, but trying the command "sensors" I get the response "No sensors found!"    I've looked at the lm_sensors Web site and it appears I need a specific module i2c-sis645.o for my SiS 648 chipset; that module doesn't appear to have been installed on my system.  The lm_sensors Web site seems oriented to the compile-from-source crowd and doesn't tell me how to install a missing module.  (I've got i2c-sis645.**c** - which I assume is the source code - on an old RedHat 7.3 partition, if that helps.)

How do I get lm-sensors up and running?

---

### Post by rapala61 on 2005-02-28
[lm_sensors how to](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors)

---

