---
title: "High temperature on Dell Studio 1555"
date: 2010-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PaBLoX_CL on 2010-01-24
I have a brand new Studio. Just got it two weeks ago. Since the beginning I notice that the touchpad gets hot after a while (maybe between an hour or two). After two hours, it's so hot that is close to make a burn.

Of course it's not the touchpad, but it's something that is JUST below.

I removed the lid and I can say for sure that it's not the HD (which is beside). Also I think it's hotter on the surface (touchpad) than on the back.

I tried the acpi and lm-sensors command, results below:

```
~$ acpi -t
Thermal 0: ok, 0.0 degrees C
Thermal 1: ok, 47.0 degrees C
Thermal 2: ok, 54.0 degrees C

~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +100.0°C)                  
temp2:       +46.0°C  (crit = +100.0°C)                  
temp3:        +0.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +105.0°C, crit = +105.0°C)
```

Anyone can help me to diagnose the problem or tell me if have a similar experience?

PS.- I can not tell if happens on Windows too, cause I deleted it as soon as I got the computer.

---

### Post by bobcollard on 2010-01-28
> **PaBLoX_CL said:**
> I have a brand new Studio. Just got it two weeks ago. Since the beginning I notice that the touchpad gets hot after a while (maybe between an hour or two). After two hours, it's so hot that is close to make a burn.

Of course it's not the touchpad, but it's something that is JUST below.

I removed the lid and I can say for sure that it's not the HD (which is beside). Also I think it's hotter on the surface (touchpad) than on the back.

I tried the acpi and lm-sensors command, results below:

```
~$ acpi -t
Thermal 0: ok, 0.0 degrees C
Thermal 1: ok, 47.0 degrees C
Thermal 2: ok, 54.0 degrees C

~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +100.0°C)                  
temp2:       +46.0°C  (crit = +100.0°C)                  
temp3:        +0.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +105.0°C, crit = +105.0°C)
```Anyone can help me to diagnose the problem or tell me if have a similar experience?

PS.- I can not tell if happens on Windows too, cause I deleted it as soon as I got the computer.
Have you heard your fan on the CPU running at all?  That is the main high temperature problem area.  Your temperatures look like they are in normal operating range.  You might try a cooling pad under the laptop to take away some more of the case's heat.

---

### Post by PaBLoX_CL on 2010-01-28
I think is actually working, I couldn't find a way to know if the fan is actually working. I think it is (I hear a noise, but it's very low), but I don't know which app can control that.

Do you how can I check if it is actually working?

---

### Post by bobcollard on 2010-01-28
> **PaBLoX_CL said:**
> I think is actually working, I couldn't find a way to know if the fan is actually working. I think it is (I hear a noise, but it's very low), but I don't know which app can control that.

Do you how can I check if it is actually working?
Try the following link.  It will give you a way to control fan speed and check if fan is running :

[http://ubuntuforums.org/showthread.php?t=842775&highlight=fan+speed](http://ubuntuforums.org/showthread.php?t=842775&highlight=fan+speed)

---

### Post by pablo180 on 2010-01-29
> **PaBLoX_CL said:**
> I have a brand new Studio. Just got it two weeks ago. Since the beginning I notice that the touchpad gets hot after a while (maybe between an hour or two). After two hours, it's so hot that is close to make a burn.

Of course it's not the touchpad, but it's something that is JUST below.

I removed the lid and I can say for sure that it's not the HD (which is beside). Also I think it's hotter on the surface (touchpad) than on the back.

I tried the acpi and lm-sensors command, results below:

```
~$ acpi -t
Thermal 0: ok, 0.0 degrees C
Thermal 1: ok, 47.0 degrees C
Thermal 2: ok, 54.0 degrees C

~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +100.0°C)                  
temp2:       +46.0°C  (crit = +100.0°C)                  
temp3:        +0.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +105.0°C, crit = +105.0°C)
```

Anyone can help me to diagnose the problem or tell me if have a similar experience?

PS.- I can not tell if happens on Windows too, cause I deleted it as soon as I got the computer.

Those temperatures look pretty normal. My processor averages around 45-55C, peaking at around 60-65C when it is working hard. Even at low temperatures for the processor the touch pad does get hot after an hour or two, not sure whether that is a laptop thing, or just a Dell thing.

---

### Post by PaBLoX_CL on 2010-01-29
> **bobcollard said:**
> Try the following link.  It will give you a way to control fan speed and check if fan is running :

[http://ubuntuforums.org/showthread.php?t=842775&highlight=fan+speed](http://ubuntuforums.org/showthread.php?t=842775&highlight=fan+speed)

Thanks for the link, I'm going to take a look soon :)

> **pablo180 said:**
> Those temperatures look pretty normal. My processor averages around 45-55C, peaking at around 60-65C when it is working hard. Even at low temperatures for the processor the touch pad does get hot after an hour or two, not sure whether that is a laptop thing, or just a Dell thing.

That would be a very weird "feature", don't you think so? My previous laptop, a Inspiron 1501 never had that kind of problems.

---

### Post by SecretCode on 2010-01-29
I agree those temperatures look fine. But even in normal operation, a lot of heat is generated, especially on notebooks, and has to escape somewhere. 

Can you find the air vents? (Typically at the back or the sides.) Naive logic tells me if the system is running too hot, and the fans are working, the vented air should also be very hot. If your touchpad is hotter than any of the air vents, you might have a fan problem.

---

### Post by PaBLoX_CL on 2010-01-29
> **SecretCode said:**
> I agree those temperatures look fine. But even in normal operation, a lot of heat is generated, especially on notebooks, and has to escape somewhere. 

Can you find the air vents? (Typically at the back or the sides.) Naive logic tells me if the system is running too hot, and the fans are working, the vented air should also be very hot. If your touchpad is hotter than any of the air vents, you might have a fan problem.

I'd say they are working, I hear a very low noise, but it doesn't change before the OS is loaded. Using my naive logic (:P), I suppose the fan speed shouldn't be different when I turn on the computer than using Ubuntu.

The other thing is that I don't know how many fans this laptop have. Do you know a way to check that?

---

### Post by SecretCode on 2010-01-29
Looking through the air vents in the case? :)

---

### Post by PaBLoX_CL on 2010-01-29
Haha, funny xD. The problem is that on the back there are four vents, two of them aren't fan (that's the lid you can easily remove to access to the RAM).

I meant something through software :P

---

### Post by maximus.bobba on 2010-02-19
I suggest u get a laptop cooler. i have the very same laptop and yes it does heat up a lot while playing games.  So, i bought a CollerMaster U2 cooling pad. works Brilliantly! has 2 repositionable fans. i kept one right underneath the RAM and the cpu. Moreover the Build is aluminum. so absorbs heat well.

---

### Post by beckx020 on 2010-02-22
I am having this type of problem with my Studio xps 1640.  Boot Ubuntu (or Mint8) 9.10 and even just leaving it sit there, the system gets hot.  Almost (really!!!!) burns your palms to try to type.  The fan is running in the system.  My laptop is on a cooling fan that is controlled by a heat sensor and it starts running full blast too as the laptop heats up.

This doesn't happen using Win7.  The system will turn on it's fans as needed and usually never full blast.  The cooler runs it's fans on very low 99% of the time.

I don't know what version to try to run to fix the problem.  There are many bug reports on this "hot" problem.

---

### Post by nishant.singh28 on 2010-03-02
The heating is no PROBLEM. The WiFi and the Bluetooth modules are right below the touchpad so it becomes a bit hot. No problems whatsoever. Yeah if you feel your notebook will get damaged(rest assured it won't), you can go for a notebook cooler as I did(because I do a lot of CPU and Memory intensive jobs) but even a simple acrylic one will bring down temperatures easily. I myself have one with 3 fans that I bought  for Rs.300(and the fans are illuminated by blue LED's:D). Any temperature for the hardware below 70 is ok and for HDD is below 55.
And any normal notebook, including this one has a single fan that cools the Processor, GPU, NorthBridge and the SouthBridge.

---

### Post by zliefer on 2010-03-03
I use a Dell also ... It gets pretty hot with any operating system. I find not having so many browser tabs open at once helps cool it down ...  especially ones utilizing Shockwave and/or Java.

---

### Post by PetrZ on 2010-05-01
Hi guys, 

I have a Studio 1537 (P8600, Radeon HD3450, 4GB DDR2 800MHz dual channel) and I have this kind of problems too. However, only in Linux.

It appears to me like the graphic card driver would be the main source of problems. I used to run Ubuntu 9.04 on it without the proprietary ATI driver (I used just the built-in Linux one) and that leaves all 3D graphic effects disabled. Actually at that configuration, the the main graphic computing tasks seems not to be done by the GPU at all. This configuration worked pretty well, but I used linux only for programming at that time. Everything else was a problem, even running a simple JavaScript simulation in a web-browser drove the laptop hot.

Several moths ago, I upgraded my Linux to 9.10 and gave the proprietary Linux driver a try. And I am pretty sure, that the it is not so good optimized like the one for Win Vista. Although I get all those graphic effect now, the computer get pretty hot, especially when watching videos.

I am using lm-tools for monitoring the temperatures and the GPU temperature is mostly the highest one with values like 75°C being no exemption. (a normal 50 minutes long movie). The problem is, that somehow, the fan speed in linux is not coupled to the GPU temperature, otherwise I cannot explain to myself why the notebook does not switch to the maximal revolutions when the GPU temperature climbs that high. I have tested it and even at 85°C the fan was not turning with its maximal frequency.

I know that it should be possible to change the critical temperature values which determine the fan speed. But I still have not figured out where they are. And also, the "sensors" info-output in my case is quiet poor: 

acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +100.0°C)                  
temp2:       +49.0°C  (crit = +100.0°C)                  
temp3:       +52.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +44.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +100.0°C, crit = +100.0°C) 

So far I have seen from other users, they have much more information there, like CPU voltage, fan speeds and so on. Does anyone know what to install to get all the extra information?


And also, where are the critical temperatures stored? I would like to change them to in order get my fan speed to react more sensitively on the GPU temperature.

Somebody wrote there that it helps to held the number of opened firefox windows at a small number. I made the same experience. Isn't it strange? I mean, internet browsing does not need so much resources. At windows, I can have tens of browser windows opened at computer gets neither to warm, nor it starts freezing. Here, I open 5 and the computer behaves like an old single-core notebook with not enough operating memory.

I really think ATI is just not trying hard enough to release a good driver for Linux. It seems, like the CPU and other resources would have to perform calculations done by the GPU in windows. Any different/same experiences to this?

Otherwise, I used to use windows for many years, but after a few months of using linux, I have to admit that windows cannot compete with it. I hope, the driver problems will improve with new versions of Ubuntu and I will be able to forget about windows completely.

Thanks,
Petr

---

