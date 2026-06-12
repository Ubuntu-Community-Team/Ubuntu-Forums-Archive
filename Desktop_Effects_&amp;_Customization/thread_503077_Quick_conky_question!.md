---
title: "Quick conky question!"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by Del Piero on 2007-07-17
Yesterday i installed lm sensors according to a guide i found on this forum and they worked pefectly. I also installed hddtemp which also work fine.

When i type > Sensors in terminal i get this:

> 
adm1027-i2c-0-2e
Adapter: SMBus I801 adapter at c800

V1.5:      +1.452 V  (min =  +1.42 V, max =  +1.58 V)   ALARM
VCore:     +1.509 V  (min =  +1.45 V, max =  +1.60 V)   ALARM
V3.3:      +3.304 V  (min =  +3.13 V, max =  +3.47 V)   
V5:       +5.202 V  (min =  +4.74 V, max =  +5.26 V)   
V12:      +12.484 V  (min = +11.38 V, max = +12.62 V)   
CPU_Fan:      0 RPM  (min = 4000 RPM)                     ALARM
fan2:         0 RPM  (min =    0 RPM)                     
fan3:         0 RPM  (min =    0 RPM)                     
fan4:         0 RPM  (min =    0 RPM)                     
CPU:      +40.00°C  (low  =   +10°C, high =   +50°C)       
Board:    +39.50°C  (low  =   +10°C, high =   +35°C)     ALARM 
Remote:   +41.75°C  (low  =   +10°C, high =   +35°C)     ALARM  
CPU_PWM:   255
Fan2_PWM:  255
Fan3_PWM:  101
vid:      +1.525 V  (VRM Version 9.0)

and when i type: > sudo hddtemp /dev/sda i get this:

> /dev/sda: ST3160211AS:  48°C

Now i have 2 questions:

What to put inside the ${} to make conky read my cpu temp?

What line to use and how to make conky read my hdd temp?

---

### Post by notwen on 2007-07-17
You could try looking at this [thread]("http://ubuntuforums.org/showthread.php?t=281865") and see how others have their sensors setup in conky.  I have also attached two links, one to conkys home page and the other for conky's variables page.  The variables are likely outdated, so I suggest checking out other ppl's conkyrc files and the output shown in their screen shots from my link above.

[conky homepage]("http://conky.sourceforge.net/")
[conky variables]("http://conky.sourceforge.net/variables.html")

---

