---
title: "Normal CPU temperature values?"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by luisjorge on 2007-08-27
Hi everyone!

I have a Dell Inspiron 630m notebook with Intel Pentium M 1.73GHz processor, and I was wondering if anyone knows which is the normal temperatures for this CPU. 
I'm running Ubuntu feisty, with scaling enabled and it usually stays at 46-48°C, reaching up to 60°C with intense working.

Also, how reliable is the ACPI reading from the GNOME panel Sensors Applet?

Thanks in advance! :)

---

### Post by S15_88 on 2007-08-27
on my 640m specs below, i'm gettinng average of between 33 and 36 degrees but that's because i'm sitting on my sofa right next to a huge airconditioner pumping out 19 degree clecius air.  but usually in an average room such as 24-26 i get 42-46 which is normal i've actually gotten my cpu upto 72 degrees before.  it has alot to do with the temperature of the surrounding environment.  but 46-48 is a nice range.  i know in windows vista mine idles at 55-60 it gets so freakin hot!  and to be honest i have no idea the accuracy of the ACPI readings but i trust them  haha

Thanks, Alain

---

### Post by jacob01 on 2007-08-27
how would i go about checking mine are there integrated censors or is there a separate piece of hardware i have to install

---

### Post by Paulmd on 2007-08-27
> **luisjorge said:**
> Hi everyone!

I have a Dell Inspiron 630m notebook with Intel Pentium M 1.73GHz processor, and I was wondering if anyone knows which is the normal temperatures for this CPU. 
I'm running Ubuntu feisty, with scaling enabled and it usually stays at 46-48°C, reaching up to 60°C with intense working.

Also, how reliable is the ACPI reading from the GNOME panel Sensors Applet?

Thanks in advance! :)

I wouldn't worry about the temperatures in the 40s, but that 60 is bad. Processor death starts occurring in the 70s, (varies by model).

Make sure that the fans are working properly and the computer is free of dust in the vents. Also... a laptop shouldn't really go on your lap, or a sofa, or a blanket. The cooling is interfered with. Ambient temperature is also a big part of the equation. If the room is already in the 30s, then of COURSE your processor is going to be warm.

---

### Post by mtbsoft on 2007-08-27
Does anyone have any opinions on those laptop cooling pads, the non-powered ones?  e.g. [http://www.pccasegear.com/prod5622.htm](http://www.pccasegear.com/prod5622.htm)

---

### Post by mtbsoft on 2007-08-27
dup.

---

### Post by luisjorge on 2007-08-28
Hello everyone! Thanks a lot for the info. I checked my cpu's specs on intel and found out that the max temperature for it is 100°C.... so I don't know if I should worry about going up to 60's during intense work or gaming.
By the way, I usually use my laptop on a table, and have a cooling base with a couple of fans, and sitting still without doing anything, the cpu reads 45°C, so maybe that's the normal temperature??
I've seen a lot of posts regarding this, and each processor shows different temperatures, some in the 20's and some even on the 50's, so I don't know for mine which is normal:)

Regarding that cooling pad, well, it looks promising... It doesn't say precisely how it works, but it seems to be some sort of chemical/physical reaction, so it could work. I happen to have a LapCool2, which has 2 fans on it and I'm pretty happy with it:).

Thank you all for the information, but does anyone know of a chart or something that could show the normal and excessive temperatures for specific cpu's?

Thanks in advance!

Luis Jorge.

Oh, and I almost forgot! I checked the fan of my laptop and it works fine, and without dust in the vents. Thanks!

---

### Post by Paulmd on 2007-08-29
> **luisjorge said:**
> Hello everyone! Thanks a lot for the info. I checked my cpu's specs on intel and found out that the max temperature for it is 100°C.... so I don't know if I should worry about going up to 60's during intense work or gaming.
By the way, I usually use my laptop on a table, and have a cooling base with a couple of fans, and sitting still without doing anything, the cpu reads 45°C, so maybe that's the normal temperature??
I've seen a lot of posts regarding this, and each processor shows different temperatures, some in the 20's and some even on the 50's, so I don't know for mine which is normal:)

Regarding that cooling pad, well, it looks promising... It doesn't say precisely how it works, but it seems to be some sort of chemical/physical reaction, so it could work. I happen to have a LapCool2, which has 2 fans on it and I'm pretty happy with it:).

Thank you all for the information, but does anyone know of a chart or something that could show the normal and excessive temperatures for specific cpu's?

Thanks in advance!

Luis Jorge.

Oh, and I almost forgot! I checked the fan of my laptop and it works fine, and without dust in the vents. Thanks!


That cooling pad: it relies on what is called phase change. A change in the state of matter, from solid, to liquid, or liquid to solid, or liquid to gas, or whatever. For example: it takes energy to turn 32 degree (f) ice into 32 degree water.  


It uses the same principle, only the phase change happens at a higher temperature. The pad absorbs heat **even though it is not getting warmer, the core is 'melting'**. It cannot do so indefinitely (it stops when all the H2O is liquid, after which the pad gets warmer), so that type of pad must be allowed to "recharge" at room temperature. Think of it as an ice pack. 
 
It is useless if the ambient temperature is above the melting point of the core material. Which is pretty warm.

The pad you pointed to also works in a second way. As a heat sink, it  facilitates the transfer of heat into the surrounding environment. This may allow a greater time between recharges. Or may, in some cases allow sessions with the pad to last indefinitely. I wouldn't count on it, your computer is WARM.



One problem with both active and passive cooling pads is the design of the laptops themselves.  In the vast majority of laptops, the CPU is on the 'top' side of the laptop's motherboard. The pad is on the bottom. 


I went and checked processorfinder.intel.com, and it seems that your processor indeed can get 100 deg c before frying. It it by far the highest number i've seen. That being the case, i wouldn't worry about 60 for the processor. 

70ish is a more usual number, like THIS chip.

[http://processorfinder.intel.com/details.aspx?sSpec=SL7KD](http://processorfinder.intel.com/details.aspx?sSpec=SL7KD)


Still.... it might be worthwhile it point out that the "thermal specification" is the absolute limit for survival of the processor. It will be unstable well below that number.

---

### Post by mtbsoft on 2007-08-29
Thanks for the info. on the pads, I might invest in one just to act as a thermal barrier between my legs and the laptop if nothing else!  

I've managed to get the i8kutils working well on my box now which has allowed me to configure the fans to my own parameters so I'm happier now, I can also switch my processor scaling settings to help run it it cooler when necessary too (though a little slower).

---

