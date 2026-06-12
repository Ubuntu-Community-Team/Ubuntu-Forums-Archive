---
title: "Losing mind over losing ticks.."
date: 2006-02-08
forum: Desktop Environments
---

### Post by n0ah on 2006-02-08
Recently my whole system locked up, bad sectors and such.. what a pain in the ***..

every so often in my dmesg I find the following..

Losing some ticks... checking if CPU frequency changed.

and I'm not sure what it is, what causes it.. or most importantly.. how to fix it.

Anyone have any idea?


System Setup: 
--------------
AMD Athlon 64 3200+
1GB DDR 400MHz RAM
MSI K8N NEO4/SLI mobo
Asus GeForce 6600GT 128MB
2x 160GB Western Digital SATA
1x 160GB Western Digital IDE
LG 16x DVD RW

---

### Post by dalee on 2006-02-08
Hi,

I'm going to try and hazard a pure guess here. You might be having a problem with your power supply. It might not be producing even enough power.

CPU freq is dependent on voltage. So if your power supply is a bit flakey, the voltages could be bouncing up and down, causing the CPU to vary.

A good multi-meter can be used to test the PS, unloaded and loaded. It may show if it is at fault. *****WARNING***** IF YOU ARE NOT COMFORTABLE AND EXPIRIENCED AT TESTING ELECTRICAL DEVICES UNDER LIVE POWER DO NOT TRY IT!!!! THERE IS ENOUGH POWER TO INJURE OR EVEN KILL YOU INSIDE THE BOX!!!!!!

Of course you can also swap it out and try another one to see if the problem goes away.

Again, this is a guess. without hands-on it is hard to tell

Good Luck!!!!!
dalee

---

### Post by RAOF on 2006-02-08
[QUOTE=n0ah]...
Losing some ticks... checking if CPU frequency changed.
...[/QUOTE]
This is not necessarily an error message.  Since you're running a athlon64, you will by default be running powernowd, which controls the Cool'n'Quiet frequeny/voltage scaling of the processor.  It will drop the frequency/voltage of your processor when idle (so it runs cooler, uses less power) and ramps it back up to maximum when it's being used.  This can cause the message.

---

### Post by n0ah on 2006-02-08
@dalee
Yeah I'm comfortable with tinkering and testing.. but I've got a 550W PSU in there.. it should be running just fine I would think..

@raof
Thanks for pointing that out.. i'll mess around in the bios and turn off the bios-run cool'n'quiet settings and see if the two (powernowd & bios) are conflicting or something perhaps..

---

