---
title: "Lib sensors mostly correct?"
date: 2009-02-17
forum: General Help
---

### Post by Kain000 on 2009-02-17
I just installed the gnome sensors applet to view my cpu and HDD temps via the gnome pannel.    

Libsensors is where it is geting my cpu's temp and I was just wondering where this is reading from on the hardware.

On my desktop the libsensors CPU temps ALWAYS display 40C but I've checked in the BIOS to find it was really 70C!!!   not exactly conforting.

how can I correct this error in reading.

And where is 40C coming from anyhow?  Perhaps it's the wrong sensor, ie: the board temp vs the cpu temp?

---

### Post by cariboo on 2009-02-17
It could be that your sensors are not supported, when you run sensors at the command line do you see something like this?

```
Sys Temp:    +38.0°C  (high = -101.0°C, hyst = -58.0°C)  ALARM  sensor = thermistor
CPU Temp:    +42.0°C  (high = +75.0°C, hyst =  +0.0°C)  sensor = thermistor
AUX Temp:    +46.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
```

In the output above you see sensor = thermistor, my server has sensors = transistor.

Jim

---

### Post by Kain000 on 2009-02-17
> **cariboo907 said:**
> It could be that your sensors are not supported, when you run sensors at the command line do you see something like this?

```
Sys Temp:    +38.0°C  (high = -101.0°C, hyst = -58.0°C)  ALARM  sensor = thermistor
CPU Temp:    +42.0°C  (high = +75.0°C, hyst =  +0.0°C)  sensor = thermistor
AUX Temp:    +46.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
```

In the output above you see sensor = thermistor, my server has sensors = transistor.

Jim



```
sean@sean-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +35.5°C  (crit = +89.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +100.0°C, crit = +100.0°C) 
```

This is what I get,

the core 0 and core 1 say adapter is ISA where as the other one is "virtural?"

what does this mean?  an estimation?

---

### Post by Kain000 on 2009-02-17
alright i'm back home with the desktop that was giving me the Cpu temp problems.

Its a quad core so I would expect to see a temp for each core like the duel core in my laptop reported(see post above)

however when I run sensors I get only one temp, 

```
sean@sean-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)    
```

for the virtual device.

Not sure what to make of this or where to go from here.

---

### Post by Kain000 on 2009-02-17
Anyone have a better program to monitor system temps???

This is a real pain to have to re-boot and check the bios when I want to know how hot my system really is.

---

### Post by DeMus on 2009-02-17
> **Kain000 said:**
> Anyone have a better program to monitor system temps???

This is a real pain to have to re-boot and check the bios when I want to know how hot my system really is.

You could give this a try, see how it goes:
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors]()
It's not my story, I have used it and it does work with one exception: you do have to re-boot some more than written in the text.
Then I use the sensors-applet (installable through Synaptic) to show me the temps in the upper panel.

---

### Post by dcstar on 2009-02-18
> **Kain000 said:**
> I just installed the gnome sensors applet to view my cpu and HDD temps via the gnome pannel.    
.......?

```
man sensors-detect
```

---

### Post by sdennie on 2009-02-18
This is probably a bug in your BIOS.  I had a machine that also displayed 40C using "acpi -t".  Those numbers are gotten directly from the BIOS by the kernel so the BIOS is simply reporting the wrong temperature (or reporting it in a non-standard part of the BIOS at least).

---

### Post by Kain000 on 2009-02-18
> **sdennie said:**
> This is probably a bug in your BIOS.  I had a machine that also displayed 40C using "acpi -t".  Those numbers are gotten directly from the BIOS by the kernel so the BIOS is simply reporting the wrong temperature (or reporting it in a non-standard part of the BIOS at least).

alright, but then why would the BIOS level health status screen tell me that the actual CPU temp is 70C?

Oviously there is a sensor that IS reading the CPU temp and the bios know about it but the kernel is reading somthing that is not a sensor, perhaps a voltage or frequency or just an error.


Does anyone know how to point the kernel to another sensor?

---

### Post by Kain000 on 2009-02-18
> **dcstar said:**
> ```
man sensors-detect
```

AHH haaa sir!!  thankyou for this, I mearly had to tell the lib sensors library to update by scaning the system for useable sensors!!


after that I now have like 18 new sensors to use including fan speeds and voltages!!


turns out the 40C was somthing that came labled as the AUX sensor, perhaps a southbrdige?   I would say northbridge but there was another called system and It was reading 96C, and I would guess that one to be it, however I do not know for sure. 

My CPU temp avg is correctly (or at least more correct) at 64C and I can see temps for each core.


thanks everyone for your help and espacially Dcstar

---

### Post by dcstar on 2009-02-19
> **Kain000 said:**
> 
.........
turns out the 40C was somthing that came labled as the AUX sensor, perhaps a southbrdige?   I would say northbridge but there was another called system and It was reading 96C, and I would guess that one to be it, however I do not know for sure. 

My CPU temp avg is correctly (or at least more correct) at 64C and I can see temps for each core.


thanks everyone for your help and espacially Dcstar

You're welcome, BTW that 40C reading seems to be common to a lot of systems as well as useless, at least with all the MB data you now have the accurate info available.

All those sensors packages need a big "Run sensors-detect" message when you install them!

---

