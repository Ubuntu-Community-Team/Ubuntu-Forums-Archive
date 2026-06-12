---
title: "If the computer Overheated..."
date: 2009-01-11
forum: General Help
---

### Post by Trzone on 2009-01-11
I am wondering if my computer overheated (8.5 years old) Basically a fan or something went, would ubuntu detect the dangerous temperatures (and shut down) or would the computer still run hotter and hotter till something failed?

---

### Post by jflaker on 2009-01-11
> **Trzone said:**
> I am wondering if my computer overheated (8.5 years old) Basically a fan or something went, would ubuntu detect the dangerous temperatures (and shut down) or would the computer still run hotter and hotter till something failed?

I would say no

The systems had very little self diagnostics and would just run until something in the circuit popped.

---

### Post by electrogeist on 2009-01-11
Ubuntu out of the box?  Not sure but leaning towards no
Can it be set up that way?  Yes.  Some motherboards will shut it down too

Will the CPU still work if this happened?  Probably just fine if Intel.  Probably fried if AMD.

---

### Post by Cresho on 2009-01-11
This would be a bios feature.  In the bios, You have an option to shut the power if it overheats such as cpu, etc.  I think it's fine if you power it on.

My girlfriends laptop has no fan since the bearings burned out on the fan in her laptop.  Her pc has power management so if it overheats, it will let her know.  It still runs fine.  On a pc, if your cpu still runs, its fine.

---

### Post by aesis05401 on 2009-01-11
I had this issue - modern CPUs have a thermal shut-off.

You can usually access the temp reading and often some settings through the BIOS. 

I had an MSI board that also kept a date of the last time the thermal protection was tripped.  There are some utilities that allow for viewing this information from within Windows if you have hardware that supports this functionality, there may be something similar in Ubuntu, but I have not run into it yet.

---

### Post by Trzone on 2009-01-11
There are hardware sensors within the bios, i thikn it's set to watch it, i'm hoping it would shut off, but it just shows the temperature.  the "sensors" command in ubuntu shows the temperature as recorded by the sensors.
It's only curiousity! heh

---

### Post by aesis05401 on 2009-01-11
> **Trzone said:**
> the "sensors" command in ubuntu shows the temperature as recorded by the sensors.

Nice tip. sudo apt-get install lm-sensors threw a bunch of errors, on makedev operations, but ran despite this. 

I will have to research the errors to see what they impact, but for just grabbing your core temps it works out of the box.

---

