---
title: "lm-sensors and Core I7"
date: 2009-02-01
forum: General Help
---

### Post by dax2112rush on 2009-02-01
Hi all,

I just bought a Core i7 system and I'd like to have some CPU temperature readouts. I tried using lm-sensors (last version from Jaunty repository) and sensors-detect can't find any sensor.

What would I need to do in order to have core i7 support into lm-sensors?
Would I have to build a new debian package with SVN version of lm-sensors?
If so, is there a nice tutorial demonstrating how to upgrade a ubuntu package to latest SVN version? (I once tried to update jackd package and failed miserably...)

CPU: Core i7 920
Motherboard: Asus P6T (not Deluxe edition)
running Ubuntu 8.10 x86-64 on 2.6.27-9-generic kernel!

Thanks
Ric

---

### Post by hooiberg on 2009-02-13
Recently I purchased a p6t deluxe with an i7 920. My lm-sensors does not find any sensors as well. This makes overclocking slightly precarious at best. I assume that the Greater Gods of Ubuntu will fix this shortly, otherwise I will not run my prcessor at full power ;)

---

### Post by JuniorJack on 2009-02-18
Hi,

I have the same problem with Asus P6T Deluxe and i7 920. I am running 64
bit version of Ubuntu.

I have followed [this]("http://ubuntuforums.org/showthread.php?t=2780") guide.

Here the only thing detected:

Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `to-be-written')

Everything else is marked as 'No'. I have full log if needed.

Regards

---

### Post by rbmorse on 2009-02-18
According to this:

[http://www.phoronix.com/scan.php?page=news_item&px=NzA2NA](http://www.phoronix.com/scan.php?page=news_item&px=NzA2NA)

a new version of lm-sensors is due shortly that will add more supported hardware to the suite.

---

### Post by kc8kod on 2009-02-24
New hardware support would be nice, I just built a computer with an Asus P6T and Core i7 920 and realized that it knew nothing of the sensors.

---

### Post by thedavis on 2009-02-25
I'm stuck too :( xDD

Anybody tested the 3.0.3 version?

I have a i7 & Asus P6T Deluxe

> Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.


jarl!

---

### Post by thedavis on 2009-03-02
Guys I think I do it :)

> coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +40.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +40.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +41.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +39.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +39.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +39.0°C  (high = +80.0°C, crit = +100.0°C)  

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.01 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.46 V  (min =  +1.00 V, max =  +0.84 V)   ALARM
AVCC:        +3.36 V  (min =  +0.00 V, max =  +0.83 V)   ALARM
3VCC:        +3.33 V  (min =  +0.51 V, max =  +0.80 V)   ALARM
in4:         +1.70 V  (min =  +0.00 V, max =  +1.09 V)   ALARM
in5:         +2.04 V  (min =  +0.77 V, max =  +0.70 V)   ALARM
in6:         +4.99 V  (min =  +1.74 V, max =  +0.03 V)   ALARM
VSB:         +3.38 V  (min =  +1.62 V, max =  +1.70 V)   ALARM
VBAT:        +3.28 V  (min =  +1.46 V, max =  +3.09 V)   ALARM
in9:         +0.00 V  (min =  +0.51 V, max =  +1.55 V)   ALARM
Case Fan:      0 RPM  (min = 2636 RPM, div = 128)  ALARM
CPU Fan:    1110 RPM  (min =    0 RPM, div = 16)  ALARM
Aux Fan:    1088 RPM  (min = 5273 RPM, div = 8)  ALARM
fan4:          0 RPM  (min = 2109 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
Sys Temp:    +43.0°C  (high =  +2.0°C, hyst =  +4.0°C)  ALARM  sensor = thermistor
CPU Temp:    +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:     +9.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V


I installed last lm-sensors from source. (3.1.0)


Mini HowTo:

Get last lm-sensors source from web page: [http://dl.lm-sensors.org/lm-sensors/releases/lm_sensors-3.1.0.tar.bz2](http://dl.lm-sensors.org/lm-sensors/releases/lm_sensors-3.1.0.tar.bz2)

$ tar xzvf lm-sensors-xxx.tar.gz
$ cd lm-sensors-xxx
$ sudo make user
$ sudo make user_install

After compiling and installing, you can try:

$ sudo sensors-detect

In my case the modules to load in /etc/modules:

> 
coretemp
w83627ehf force_id=0x8860


Now you can edit /etc/sensors3.conf for change labels names etc...

I think the sys temp detected are the cpu temp, and viceversa, the cpu temp detected are the sys temp

I wish this could help anyone with a Asus P6T and i7 ;)

Sorry for my terrible english ;(

---

### Post by wallofinsanity on 2009-03-30
I have an i7 and a p6T, and installing 3.1.0 from source did the trick on getting sensors-detect to recognize my hardware.

btw, if you install bison/flex after running "make user", you have to run "make clean" before re-compiling. That was one issue I ran into.

---

### Post by thedavis on 2009-03-30
> **wallofinsanity said:**
> I have an i7 and a p6T, and installing 3.1.0 from source did the trick on getting sensors-detect to recognize my hardware.

btw, if you install bison/flex after running "make user", you have to run "make clean" before re-compiling. That was one issue I ran into.

Finally u got the sensors? :)

---

### Post by wallofinsanity on 2009-03-30
Yeah the cpu temp sensors are working, but I'm getting errors when trying to load the w83627ehf driver. Did you have to do anything special to get it to work?

---

### Post by thedavis on 2009-03-30
What modules have you enabled?

In my /etc/modules I have this:

```
#Chip drivers
coretemp
w83627ehf force_id=0x8860
```

Output:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +44.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +43.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +43.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +41.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +44.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +43.0°C  (high = +80.0°C, crit = +100.0°C)  

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.01 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.46 V  (min =  +1.00 V, max =  +0.84 V)   ALARM
AVCC:        +3.36 V  (min =  +0.00 V, max =  +0.83 V)   ALARM
3VCC:        +3.33 V  (min =  +0.51 V, max =  +0.80 V)   ALARM
in4:         +1.70 V  (min =  +0.00 V, max =  +1.22 V)   ALARM
in5:         +2.04 V  (min =  +0.77 V, max =  +0.66 V)   ALARM
in6:         +5.12 V  (min =  +0.10 V, max =  +0.03 V)   ALARM
VSB:         +3.38 V  (min =  +1.55 V, max =  +1.18 V)   ALARM
VBAT:        +3.30 V  (min =  +1.46 V, max =  +3.09 V)   ALARM
in9:         +0.00 V  (min =  +0.51 V, max =  +0.53 V)   ALARM
Case Fan:      0 RPM  (min = 2636 RPM, div = 128)  ALARM
CPU Fan:    1095 RPM  (min =    0 RPM, div = 16)  ALARM
Aux Fan:    1095 RPM  (min = 5273 RPM, div = 8)  ALARM
fan4:          0 RPM  (min = 2109 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 5273 RPM, div = 128)  ALARM
Sys Temp:    +45.0°C  (high =  +2.0°C, hyst =  +4.0°C)  ALARM  sensor = thermistor
CPU Temp:    +33.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:     +7.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
```

It's not 100% accurate, but this is better that any xD

---

### Post by wallofinsanity on 2009-03-30
Ah, got it. I didn't know where you were getting the 'force_id=0x8860' part from so I was trying to use the hex code that sensors-detect gave me.

After using your setup exactly it works. Thanks for the help!

---

### Post by thedavis on 2009-03-30
I got the code from a forum, I don't remember where exactly, but it's works :)

I remember that code is necesary for a few Asus MB ;)

---

### Post by Greyhound- on 2009-05-28
I have an Intel Core i7 on a Gigabyte GA-EX58-UD5 motherboard and am running Ubuntu 9.04. I've been trying like crazy to get lm-sensors to work but seem to be failing miserably. Could someone please tell me what I'm doing wrong? I first installed lm-sensors through the repository, ran sensors-detect.. had not luck, then I installed it from source, same thing happened again. Here's the output I get from running sensors-detect:

```
# sensors-detect revision 5666 (2009-02-26 17:15:04 +0100)
# System: Gigabyte Technology Co., Ltd. EX58-UD5

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal and voltage sensors...                       No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We have to read from arbitrary I/O ports to probe for such interfaces.
This is normally safe. Do you want to scan for IPMI interfaces?
(YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              No
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `adt7473')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `Texas Instruments THMC51'...                   No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791SD'...                           No

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: SMBus I801 adapter at 0500 (i2c-6)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6647'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `National Semiconductor LM64'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        Yes
    (confidence 6, not a hardware monitoring chip)
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `adt7473':
  * Bus `NVIDIA i2c adapter '
    Busdriver `nvidia', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): 
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
```

---

### Post by RockyHope on 2009-08-12
Hi Guys, 

I've tried the method above but only seem to get the following:

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +0.94 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.40 V  (min =  +0.00 V, max =  +6.81 V)   ALARM
AVCC:        +3.30 V  (min =  +0.00 V, max =  +0.10 V)   ALARM
3VCC:        +3.26 V  (min =  +3.30 V, max =  +2.05 V)   ALARM
in4:         +1.70 V  (min =  +1.30 V, max =  +1.16 V)   ALARM
in5:         +2.04 V  (min =  +0.01 V, max =  +1.17 V)   ALARM
in6:         +5.63 V  (min =  +0.87 V, max =  +1.74 V)   ALARM
VSB:         +3.39 V  (min =  +3.97 V, max =  +0.56 V)   ALARM
VBAT:        +3.30 V  (min =  +0.02 V, max =  +2.08 V)   ALARM
Case Fan:   1125 RPM  (min = 9926 RPM, div = 8)  ALARM
CPU Fan:    1454 RPM  (min = 3515 RPM, div = 16)  ALARM
Aux Fan:       0 RPM  (min = 42187 RPM, div = 32)  ALARM
fan4:       1110 RPM  (min = 2596 RPM, div = 8)  ALARM
fan5:       1117 RPM  (min = 3245 RPM, div = 8)  ALARM
Sys Temp:    +49.0°C  (high = +18.0°C, hyst = -128.0°C)  ALARM  sensor = thermistor
CPU Temp:    +30.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:     -8.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

Any Ideas?

---

### Post by ljubomirjosifovski on 2009-10-27
Has anyone got lm-sensors working with i7 860 (and/or 870) and/or Asus p7p55 motherboard on Ubuntu Jaunty 9.04? How?  Thanks,

---

### Post by GiveLove on 2009-10-27
Hello Everyone, :)

That's a real bummer that lm_sensors is behind in software support of your hardware. But it will change eventually as the lm_sensors developers continue to add more hardware support. It's nice though that some of you have had some success by installing the latest version from their web site, or the version still in development and testing (SVN). 

At some point when your hardware is supported, one tip I found very useful to getting temperature and fan RPMS simply and easily displayed in a default Gnome desktop:

Install GNOME Sensors Applet from the repositories in Synaptic Package Manager. The package name is "sensors-applet". Here's a link to their web site for information and screenshots.
[http://sensors-applet.sourceforge.net](http://sensors-applet.sourceforge.net)

As it is installing, make sure to say yes to HDD temp boot auto start if you want your hard drive temperature available to display. This package installs lm-sensors by default. You do still have to run the command "sensors-detect" in a terminal, and then re-boot afterwards. The re-boot is necessary, or otherwise all the available sensors will not display. 

Then single right click on a panel where you want to add the sensor readings and select "Add to Panel...", and then select "Hardware Sensors Monitor". From there single right click on the sensors applet in the panel and select "Preferences". And you can start customizing which sensors you would like to see, how they are displayed and titled, and add any alarms.

I've attached a screenshot of my sensors displayed on my top panel. What you are looking at from left to right is: Hard drive temp, GPU temp, Case temp, CPU temp, Power supply fan RPM, and CPU fan RPM. And just so there is no confusion, as Gnome Sensors Applet can display sensors in the same graphical way... The next two are not sensors from this applet, but are from the "System Monitor" applet. Which is displaying hard drive read and write activity, and system load.

---

### Post by ljubomirjosifovski on 2009-10-27
[SIZE=2]Thanks for your help, GiveLove.
Yes, GNOME Sensors Applet is great (I use it as well), the System Monitor applet too.

In similar vein is the "CPU Frequency Scaling Monitor" applet, also have it docked up there. Not only it shows the frequency a core is running (in variable speed modes like "Conservative", "OnDemand", etc), one can also set the frequency the core should run on from then on. Useful on laptops that tend to overheat on long running jobs and shutdown before finishing them. ;-)

Wrt lm-sensors, not sure if this is relevant, while googling  saw [/SIZE]  [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]"2.6.31.3: coretemp module fails on i7 870 CPU" recent post at [/COLOR][/FONT][/COLOR][/SIZE][/FONT][SIZE=2][http://www.gossamer-threads.com/lists/linux/kernel/1141897](http://www.gossamer-threads.com/lists/linux/kernel/1141897). I presume lm-sensors gets the data from the coretemp module, so will have to wait for that to work, but maybe wrong - no idea who talks to whom in order to get the sensors data out.[/SIZE]

---

### Post by David W on 2009-12-04
This quick fix worked for me (core i7 on a GigaByte UD5 motherboard):

[http://forums.fedoraforum.org/archive/index.php/t-220570.html](http://forums.fedoraforum.org/archive/index.php/t-220570.html)

---

### Post by soulspit on 2010-09-26
Hi everyone,

This is a bit of an old thread, but I was struggling with not getting temperatures on a core i7 processor, and this thread helped and I thought I'd contribute in case any others stumble upon this.  I did try installing lm-sensors from the source as thedavis recommends, but it didn't work for me.  I downloaded the latest sensors-detect script and it found (finally!) some sensors, but didn't actually make any changes that made lm-sensors work.  It did, however, tip me off to the fact that simply loading the coretemp kernel module
```
sudo modprobe coretemp
```
made everything work!  I don't know if having installed the latest version of lm-sensors from source helped or not, and I don't know if it was necessary for me add coretemp to /etc/modules, but I did both of these, and 'sensors' now gives me believable temperatures for all four cores.  Now I just want to get access to my fan speed... anyone with a Dell Studio 1747 got this working?

---

### Post by Seinfeld on 2011-02-05
Hi..

I really do appreciate your help in this..
I just bought an Intel DPX558SO. Installed Core i7 960.
Using Ubuntu 10.10. With lm-sensors. The Core(2) i.e. third core is reporting 10 degrees higher than all other three cores, even at idle. 
I reinstalled the heat sink, applied a proper amount of thermal compound etc.. Still same problem. all other cores, 0,1,and 3 seem to be fine with only 1-2 degrees difference among them
lm-sensors being the only hardware monitoring software available in Linux, I don't have any other way to know. 
I don't want to install Windows for trying out Coretemp, Realtemp etc. kind of a hassle here.

Thanks a lot in advance for your help

---

