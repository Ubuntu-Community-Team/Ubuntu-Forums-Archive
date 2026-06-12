---
title: "Trouble with lm_sensors"
date: 2006-09-30
forum: Desktop Environments
---

### Post by djpenguin on 2006-09-30
I recently switched my main desktop machine from Gentoo to Kubuntu, because I wanted a system that would be easier to maintain.

Unfortunately, I am having trouble getting lm_sensors correctly configured.  I have attempted to follow [this guide](http://ubuntuguide.org/wiki/Dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29), but I do not get the results I am looking for.

Here's what the tail end of the process described in the link above results in:

```
Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `not-a-sensor' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x2f
    Chip `Winbond W83791SD' (confidence: 3)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x52
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `NVIDIA I2C Device'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x57)
    Chip `DDC monitor' (confidence: 8)

Driver `smbus-arp' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x61
    Chip `SMBus 2.0 ARP-Capable Device' (confidence: 1)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627THF Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? ISA

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
i2c-isa
# I2C chip drivers
eeprom
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see http://secure.netroedge.com/~lm78/supported.html
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
w83627hf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y
root@chilly-willy:~# sensors -s
No sensors found!

```

So now I am stuck, and I don't have any idea what to do next.  I had no trouble getting lm-sensors operational under Gentoo, so I have no clue where to start working on this problem.  Searching the Ubuntu forum has not yielded anything helpful so far.

Thanks in advance for your assistance.

---

### Post by croak77 on 2006-09-30
You first need to modprobe the modules that aren't already loaded. Example;
```

sudo modprobe i2c-i801
```

---

### Post by djpenguin on 2006-09-30
That got it, many thanks for the prompt reply.

---

