---
title: "D620 - CPU temp and FAN speed"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by Waleb on 2007-07-17
Hi there, 

I just got an Latitude D620 and it works really fine with Ubuntu (_everything_ out of the Box). I just got one Problem and thats with lm-sensors. Thats what i get after "sensors-detect":

```
Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 10c0'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
#----cut here----

```

Well, I let the script edit the /etc/modules (it did everything correct) but even after a reboot "sensors" gives me the finger: 

```
waleb@laptop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

How can I display the CPU temp and FAN speed?

---

### Post by rombel4u on 2007-07-18
this link might help

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_monitor_CPU.2C_GPU_temperatures.2C_fan_speeds_and_voltages_.28GKrellM.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_monitor_CPU.2C_GPU_temperatures.2C_fan_speeds_and_voltages_.28GKrellM.29")

---

