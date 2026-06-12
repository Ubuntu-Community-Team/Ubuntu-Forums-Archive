---
title: "Dell fan control on 64-bit"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by michael37 on 2007-08-05
I am struggling with fan control on Dell E1505 running 64-bit Fiesty Fawn.    GrellM detects CPU (using thermal_zone) and HD (using hddtemp) temperatures, but does not detect any fans.

As pointed out on many threads, i8k kernel module is not available in 64-bit Ubuntu so i8kutils don't work.

I installed lm_sensors, but they couldn't find a fan either.

What are my other options?

---

### Post by TechZilla on 2007-08-12
im also having the same issue, installed lm_sensors, yet no fan control.

the output we are getting from the sensors is because of the modules

i2c_core
k8temp

pwmconfig outputs
'/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)'

the i8k is missing from x86_64, i have also heard that this is because it is x86 specific.  my question is why? im going to look at the source if possible.  if its written in asm then that is a legit reason, but the kernel is written in C (not every module tho.)

---

### Post by saru411 on 2007-08-20
im having same issue on my vostro 1500

can we force architecture? if so an you post the codes we need to install this? any help would be useful!!!

---

### Post by kansei on 2007-09-07
*subscribes*

after months of burning myself using the laptop, I'm really getting tired of having no fan control.

I installed 'stress' and within 60 seconds core temps went from 45C to 72C!!

meanwhile the fan is chugging along at the absolute minimum speed as always.

---

### Post by michael37 on 2007-09-09
> **kansei said:**
> *subscribes*

after months of burning myself using the laptop, I'm really getting tired of having no fan control.

I installed 'stress' and within 60 seconds core temps went from 45C to 72C!!

meanwhile the fan is chugging along at the absolute minimum speed as always.

Correct, some BIOS magic makes fan go at full at 75C on my E1505, but other than that, there are literally no fan control.

---

### Post by kansei on 2007-09-09
Maybe 75 is the trigger temp for the fan to go wild. I don't think it hit 75 during my testing. Still, maintaining the temp at near 70C often is way uncomfortable. Hence why they call them 'notebooks' instead of 'laptops'. I guess when I want lap comfort I'll use my thinkpad (like right now) :P

---

### Post by saru411 on 2007-09-10
> **kansei said:**
> Maybe 75 is the trigger temp for the fan to go wild. I don't think it hit 75 during my testing. Still, maintaining the temp at near 70C often is way uncomfortable. Hence why they call them 'notebooks' instead of 'laptops'. I guess when I want lap comfort I'll use my thinkpad (like right now) :P

how about posting something useful rather than spam.

thanks

---

### Post by kansei on 2007-09-10
*rolls eyes* dude I've been looking at i8k code all morning, and you want to complain that my post was spam .. what because it didn't resolve anything? I guess your post, on the other hand, did?

To answer the question in your first post: No, there's no way to get at the rest of the sensors without the i8k module. I dug up a few threads on here from ~march or earlier and someone who appeared to be a developer working on i8k mentioned needing a 64-bit computer to run some really alpha-type testing. I haven't heard anyone mention any progress newer than that, and I PMed the guy in question offering my D620 (the only of the 25+ latitudes I have that has a core2) for testing but haven't heard back (sent the PM a couple days ago).

---

### Post by saru411 on 2007-09-11
i would just prefer that you post some of the information you came up with while digging around so others can find the information that will lead to a resolution. saying you are going to get on another "notebook/laptop" doesnt further the progress. i feel i went about asking you to give the sum of your research in a negative way. i seem to be doing that more often than not recently.

sorry for the bad vibes.

anyway i did get lm-sensors running on my laptop,vostro 1500, on a previous install of 7.04. unfortunately it didn't find any sensors on the vostro. i believe i've seen my fan come on once, but i rarely use my laptop for longer than 30 mins. i never burn cds either so i don't build up heat while im on it. that's the only reason im still running ubuntu on this laptop.

THIS IS A SERIOUS ISSUE!!!
HARDWARE COULD BE DAMAGED BECAUSE OF IT!!!!
WE NEED A FIX NOW!!!

---

### Post by kansei on 2007-09-11
acpi -V (capital "V") doesn't even give CPU temp?

output should look like this:

chris@CDL-T42:~$ acpi -V
     Battery 1: discharging, 46%, 01:03:55 remaining
     Thermal 1: ok, 48.0 degrees C
  AC Adapter 1: off-line

---

### Post by michael37 on 2007-09-11
> **TechZilla said:**
> (...)
the i8k is missing from x86_64, i have also heard that this is because it is x86 specific.  my question is why? im going to look at the source if possible.  if its written in asm then that is a legit reason, but the kernel is written in C (not every module tho.)

Yes, i8k kernel module (aka driver) is written in asm.  Feel free to parse the source posted at
[http://people.debian.org/~dz/i8k/](http://people.debian.org/~dz/i8k/).  You also find the kernel module source in the Ubuntu 32-bit kernel tree.

> **saru411 said:**
> im having same issue on my vostro 1500

can we force architecture? if so an you post the codes we need to install this? any help would be useful!!!

No, the loaded drivers must match the architecture of the running kernel.  They are not like applications which can run natively in 32-bit mode on a 64-bit OS.

***NEW*** It looks like the 64-bit Windows driver is now available.  This is a great progress since the Windows driver is based on the originaly i8k 32-bit Linux driver.  See more details at [http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

---

### Post by saru411 on 2007-09-11
> **michael37 said:**
> 

***NEW*** It looks like the 64-bit Windows driver is now available.  This is a great progress since the Windows driver is based on the originaly i8k 32-bit Linux driver.  See more details at [http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)


this is interesting. is there a way to use this windows driver on ubuntu?

---

### Post by michael37 on 2007-09-11
> **saru411 said:**
> this is interesting. is there a way to use this windows driver on ubuntu?

It's very unlikely, so unlikely that I'd say outright no.  However, if we know what the code changes were to port the driver to 64-bit Windows from 32-bit Windows, we can possibly port the 32-bit Linux driver as well.  I am not sure whether the source for the 64-bit Windows driver is available.  Need help there from someone running Windows and able to run/study i8kfan.

---

### Post by kansei on 2007-09-12
btw here is one of the other threads I had mentioned finding on the subject:

[http://ubuntuforums.org/showthread.php?t=274175](http://ubuntuforums.org/showthread.php?t=274175)

---

### Post by dyssident on 2008-01-04
I got the fan on my Vostro 1500 working perfectly using dellfand. See [this thread]("http://ubuntuforums.org/showthread.php?p=4069092").

---

