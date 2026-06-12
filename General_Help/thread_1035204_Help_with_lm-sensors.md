---
title: "Help with lm-sensors"
date: 2009-01-09
forum: General Help
---

### Post by BlueFalconWii on 2009-01-09
Hello, I installed lm-sensors in my Ubuntu Intrepid (64 bits). I can see the temperature of my 4 cores without any problem, also the temperature of my HDD and the fans.The thing is that there are 3 different temperatures called temp1,temp2 and temp3. I suppose one of them must be from the mother board temperature, but I'm not sure. Do you know to what belongs each of this temperatures?. Thanks a lot


Core2 Quad 2.4ghz
8gb DDR2 800 MHZ CL5
Mother Board Foxconn G33M
Sata2 500gb

---

### Post by Zeroberry on 2009-01-09
I'm afraid you have to figure that out yourself. They can be from outside the processor, from inside the processor, from the motherboard, from hard drives, GPU, outside GPU and so on. Check them out while cpu is at load and idle, should show which is core.

---

### Post by BlueFalconWii on 2009-01-09
I entered to the BIOS and I found that the temp2 belongs to the system temperature. Now I only need to know what means temp 1 and 3.

P.D I'm sure temp 1 and 3 aren't from any of the cores of the cpu, system temp, and HDD because I can see them with their respective names.

---

### Post by heindsight on 2009-01-09
does temp3 ever change? If not, or if it shows obviously bogus values it might not be connected to anything.

On my desktop machine sensors also showed 3 temperature readings temp1 temp2 and temp3. In my case temp1 was the CPU temperature, temp2 was a sensor on the motherboard and temp3 was not connected to anything and always read 25C. So I changed my /etc/sensors.conf to relabel temp1 to CPU_temp temp2 to MB_temp and ignore temp3.

---

### Post by BlueFalconWii on 2009-01-09
Actually, temp3 never change, it displays 128ºC always. I'm not sure to what belongs temp3, but I'm sure it doesn't belong to the system or CPU temperature because I can see these with their respective names(cpu0, cpu1, cpu2, cpu3). You give me some ideas, thanks!.

> **heindsight said:**
> does temp3 ever change? If not, or if it shows obviously bogus values it might not be connected to anything.

On my desktop machine sensors also showed 3 temperature readings temp1 temp2 and temp3. In my case temp1 was the CPU temperature, temp2 was a sensor on the motherboard and temp3 was not connected to anything and always read 25C. So I changed my /etc/sensors.conf to relabel temp1 to CPU_temp temp2 to MB_temp and ignore temp3.

---

### Post by heindsight on 2009-01-10
> **BlueFalconWii said:**
> Actually, temp3 never change, it displays 128ºC always.

Yes, my guess is that your temp3 isn't connected to anything...

---

### Post by SabreWolfy on 2009-09-08
So I guess my temp2 which shows -3 degrees C is also probably not connected to anything, except maybe the freezer :)

---

### Post by mcduck on 2009-09-08
Lm-sensors doesn't really consider what the readings are, it simply reads raw data from the sensor chip on our motherboard and outputs it. Making sure all the sensor data is assigned to correct readings and calculated correctly from the sensor data is up to you, and done by configuring the sensors.conf file. (The actual way how sensors are handled on motherboards depends on motherboard model, and even with the same sensor chip the actual implementation differs a lot. Lm-sensors only detects the sensor chip, not motherboard model, so if the sensor implementation on your motherboard is not the same as the defaults for that chip you can get pretty messed up data from lm-sensors)

If the data on those outputs doesn't change, the actual sensors probably don't even exist. If the data changes, there's some sensor but you'll still have to figure out what the sensor does, and what formula or multiplier should be used to get the correct value.

Even if all the output from lm-sensors seems sensible you probably need to at least define sensible min & max values for warnings in the sensors.conf, as the defaults are rather faulty. Voltage limits have nothing to do with actual ATX standards and often the min value is set higher than max, and fan speeds pretty much always require changing the multipliers, for example. I don't know why the default setup is so badly configured.

---

### Post by fragos on 2009-09-08
On my mobo I decided that the temp that ran in the 40 range was the CPU. The mobo temp was always much lower. The 128 is so high I doubt it's a real temp.

---

