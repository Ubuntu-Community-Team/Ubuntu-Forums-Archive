---
title: "Dell Inspiron E1505: Laptop does not run off Battery; Only with power cord."
date: 2010-02-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cyrojin on 2010-02-28
Hi; I'm new to using Linux, so bear with me :). I had installed Ubuntu 9.10 onto my Dell Inspiron E1505 (with Windows XP in another partition), and everything seemed to be fine. But when I tried to boot the laptop earlier today, it would not start on battery power. If I pulled the AC adapter cord while the computer was on; the computer would shut off like there was no battery at all. The battery is definitly being detected, at 100% charge, and no wear. I've had this problem for a few days; I had deleted the partition and did a fresh install... and eureka; the battery started working again. But as soon as it installed a giant slew of updates... it was back to square one. 

I'm kinda at my wits end here... 
I did figure out how to pull some information on the battery with Terminal.

POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12440000
POWER_SUPPLY_CURRENT_NOW=1000
POWER_SUPPLY_CHARGE_FULL_DESIGN=5200000
POWER_SUPPLY_CHARGE_FULL=5200000
POWER_SUPPLY_CHARGE_NOW=5200000
POWER_SUPPLY_MODEL_NAME= DELL00
POWER_SUPPLY_MANUFACTURER=D6000H
POWER_SUPPLY_SERIAL_NUMBER=1

If that helps at all. I appreciate any advice, or dare I say a solution, that ya'll could give me. :D

And yes, I did take out the battery, check the connectors, etc. Seems fine on that front.

---

### Post by isbiyanto on 2010-05-18
> **Cyrojin said:**
> Hi; I'm new to using Linux, so bear with me :). I had installed Ubuntu 9.10 onto my Dell Inspiron E1505 (with Windows XP in another partition), and everything seemed to be fine. But when I tried to boot the laptop earlier today, it would not start on battery power. If I pulled the AC adapter cord while the computer was on; the computer would shut off like there was no battery at all. The battery is definitly being detected, at 100% charge, and no wear. I've had this problem for a few days; I had deleted the partition and did a fresh install... and eureka; the battery started working again. But as soon as it installed a giant slew of updates... it was back to square one. 

I'm kinda at my wits end here... 
I did figure out how to pull some information on the battery with Terminal.

POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Full
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
POWER_SUPPLY_VOLTAGE_NOW=12440000
POWER_SUPPLY_CURRENT_NOW=1000
POWER_SUPPLY_CHARGE_FULL_DESIGN=5200000
POWER_SUPPLY_CHARGE_FULL=5200000
POWER_SUPPLY_CHARGE_NOW=5200000
POWER_SUPPLY_MODEL_NAME= DELL00
POWER_SUPPLY_MANUFACTURER=D6000H
POWER_SUPPLY_SERIAL_NUMBER=1

If that helps at all. I appreciate any advice, or dare I say a solution, that ya'll could give me. :D

And yes, I did take out the battery, check the connectors, etc. Seems fine on that front.

i have same problem; with lenovo 3000 g410, upgrade from 9.10 to 10.04. can anyone help me please?

---

