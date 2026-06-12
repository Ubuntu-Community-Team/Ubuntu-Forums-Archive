---
title: "Computer Temperature Monitor"
date: 2009-04-20
forum: General Help
---

### Post by cathalcummins on 2009-04-20
Running Ubuntu Studio (8.10) on an Asus M2N-MX SE board with AMD Athlon 64 X2 Dual Core Processor 4400+ inside a (fan cooled) Antec case. 


I installed the nifty little gnome applet; Computer Temperature Monitor 0.9.6.1 so I can see how my CPU is doing. Problem: The temperatures it produces are far too low, even by Antec case standards. The sensors are reading 6,-5,16,2. I don't care too much for the case temp, it's the CPU I would be concerned about. Even the highest is far too low for and idle system with said configuration.

The preferences set inside the program itself are:

Select Sensor to monitor: Kernel i2c sensors (hwmon)

I don't have a choice to change this. I was thinking if I could change this then maybe I could get more sensors and may be able to monitor my CPU.

Anybody with experience of a similar/same setup, especially with that specific board. I seem to recall having problems with this board in windows when trying to monitor the CPU.

Thanks

---

### Post by redbook4574 on 2009-04-20
Try sudo apt-get install sensors-applet
 Then add hardware sensors 
finally rund "sudo sensors-detect"

I use an m2ne with a amd 64x2 6000 and all seems fine with mine.

Hope this helps.

---

### Post by cathalcummins on 2009-04-20
That worked like a charm. 

Thank you.

AMD idles around 32C with fans on low.

Tried some heavy MATLAB calculations + video rendering simultaneuosly; about 46C.

Quite happy with that.

Do I put the [SOLVED] in the title manually?

---

