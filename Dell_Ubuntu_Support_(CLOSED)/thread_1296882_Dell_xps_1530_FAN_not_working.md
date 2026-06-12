---
title: "Dell xps 1530 FAN not working"
date: 2009-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amittalkin on 2009-10-21
hello everyone..

i'm new to ubuntu....
recently i've installed this new OS on my xps m1530 laptop from a live CD...and what i observed was my laptop getting very hot...the temperature is as high as 60c .

in **vista it is usually cool...**

one thing i observed was whenever i start my browser the fan gets switched on only when the temperature goes above 60c..

i tried many things and the outputs of the corresponding trials are as follows:

-----------------------------------------------------------------------
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +126.0°C)                  
-----------------------------------------------------------------------
when i run gkrellm ...no improvement...i cant control the fans....
----------------------------------------------------------------------
contents of /proc/acpi/fan folder are empty
---------------------------------------------------------------------
/proc/acpi/thermal_zone/THM$ ls

cooling_mode  polling_frequency  state  temperature  trip_points
-----------------------------------------------------------------------
$ cat cooling_mode 
<setting not supported>
-----------------------------------------------------------------------
$ cat polling_frequency 
<polling disabled>
-----------------------------------------------------------------------
/proc/acpi/thermal_zone/THM$ cat state 
state:                   ok
-----------------------------------------------------------------------
 /proc/acpi/thermal_zone/THM$ cat trip_points 
critical (S5):           126 C
----------------------------------------------------------------------

please please please please....some one help me out .......!!!

---

### Post by Elfy on 2009-10-21
closed duplicate here - [http://ubuntuforums.org/showthread.php?p=8139177#post8139177](http://ubuntuforums.org/showthread.php?p=8139177#post8139177)

---

