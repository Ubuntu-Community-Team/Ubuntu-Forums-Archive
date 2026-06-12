---
title: "Monitor and log power supply"
date: 2011-02-17
forum: Desktop Environments
---

### Post by Azyx on 2011-02-17
Is there any application that log voltage from the power supply, to check if it's broken, during a long time. I can see the voltage in BIOS.

run 10.04 LTS

/cheers

---

### Post by Azyx on 2011-02-17
I think I need sensors and run ```
sudo sensors-detect
```

I detect w83697hf-isa-0290 and EDID

```
Next adapter: nouveau-0000:01:00.0-1 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
[COLOR=Red]**Probing for `EDID EEPROM'...                                Yes**[/COLOR]
    (confidence 8, not a hardware monitoring chip)

```

but in the end there only says:

```
To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
[COLOR=Red]w83627hf[/COLOR]
#----cut here----
```

When I the run sensor I get rabbish-values like this:

```
$ sensors
[COLOR=Red]w83697hf[/COLOR]-isa-0290
Adapter: ISA adapter
in0:         +1.65 V  (min =  +1.31 V, max =  +1.06 V)   ALARM
in2:         +3.39 V  (min =  +2.21 V, max =  +0.13 V)   ALARM
in3:         +3.04 V  (min =  +1.02 V, max =  +2.90 V)   ALARM
in4:         +3.15 V  (min =  +2.67 V, max =  +0.13 V)   ALARM
in5:         +0.56 V  (min =  +0.64 V, max =  +2.05 V)   ALARM
in6:         +0.78 V  (min =  +3.87 V, max =  +0.06 V)   ALARM
in7:         +3.36 V  (min =  +1.15 V, max =  +0.58 V)   ALARM
in8:         +3.65 V  (min =  +0.08 V, max =  +0.35 V)   ALARM
fan1:       2191 RPM  (min = 48214 RPM, div = 4)  ALARM
fan2:          0 RPM  (min = 2343 RPM, div = 4)  ALARM
temp1:       +35.0°C  (high =  +0.0°C, hyst =  +2.0°C)  ALARM  sensor = thermistor
temp2:       +46.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled

```

What Is wrong?

PS. I Thinnk I need working sensors before I find an application that monitor voltage during a longer time of time to see if the power supply work in properly.

---

### Post by Johnny3 on 2011-02-22
You can install Xsensors software center.
New bee way.
GB Johnny

---

### Post by Azyx on 2011-02-22
> **Johnny3 said:**
> You can install Xsensors software center.
New bee way.
GB Johnny

Thanx, that was nice, but my problem with false voltage are still there. My co,puter would not start if I don't have 12V.

---

### Post by Azyx on 2011-02-23
seems to be a naer 1 year old bug...

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/563114](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/563114)

Is there a fix for it?

---

