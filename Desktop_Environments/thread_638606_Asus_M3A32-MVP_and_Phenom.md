---
title: "Asus M3A32-MVP and Phenom"
date: 2007-12-12
forum: Desktop Environments
---

### Post by jmontelius on 2007-12-12
Hi,

 I've ordered some new things that I'm planning to run Kubuntu on. Does anyone have any experience getting the Asus M3A32-MVP up and running? 

I'll post my own experience as soon as I have the things put together. 

  J

---

### Post by notbuu on 2007-12-19
hello!

i am also interested on this mainboard. i will buy this one in the near future. if you can provide some informations about lm-sensors working and some information about the other features of this mainboard, please let us know.

do you have the wifi edition or the normal one?

thanks and regards

notbuu

> **jmontelius said:**
> Hi,

 I've ordered some new things that I'm planning to run Kubuntu on. Does anyone have any experience getting the Asus M3A32-MVP up and running? 

I'll post my own experience as soon as I have the things put together. 

  J

---

### Post by jmontelius on 2007-12-20
Still waiting for the mother board. Got the Phenom, a Ausus EN8600GT SILENT/HTDP/512M graphics card and all the other parts. I'm told the mother board will be here next week so will not have time to test things before new years.

Doubt that lm-sensors will work out of the box. I'm not intending to oc this and I think I have enough cooler and fans to keep it cool and quite so I will survive. I will of course give it a try. 

I'll keep you posted.

---

### Post by sfagmenos on 2007-12-23
I have order these two as well an i am planninig to install them Ubuntu 7.10
but i have read ina some other fora that Linux ahve some problems ( not that windows have fixed it :p) with L3 Cahe and I'm very worried adout what to do ??

---

### Post by Kingsfan on 2007-12-23
something about hitting 100% load on all 4 cores will give you BSOD, unlikely you'll load the cpu that much but they have released BIOS fixes for this, apparently they will drop performance by 10% though, the problem is supposed to be corrected in the B3 stepping which should come out Q1 08

---

### Post by sfagmenos on 2008-01-02
i have installed ubuntu 7.10 AMD 64 and i don,t have any problem occured while running applications
i have installed the  2.6.22-14-generic kernel and all is running smoothly :)

---

### Post by jmontelius on 2008-01-25
Motherboard finally arrived and everything went smoothly. Kubuntu 7.1 installed without problems.  lm-sensors works ok from what I can tell but does not recognize sensors from the cpu (Phenom), only the motherboard. Not an expert in this but this is some output:

>sudo sensors-detec
  :
Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): YES
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No


>sudo sensors
it8716-isa-0e80
Adapter: ISA adapter
VCore:     +1.23 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
VDDR:      +3.26 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +4.97 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:     +12.16 V  (min =  +0.00 V, max = +16.32 V)   ALARM
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:      +6.85 V  (min =  +0.00 V, max =  +5.99 V)   ALARM
VBat:      +3.23 V
fan1:     1415 RPM  (min =    0 RPM)
fan2:        0 RPM  (min =    0 RPM)
fan3:        0 RPM  (min =    0 RPM)
temp1:       +41°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   ALARM
temp2:       +34°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   ALARM
temp3:       +54°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   ALARM
vid:      +0.000 V

---

### Post by Twintop on 2008-01-28
> **jmontelius said:**
> lm-sensors works ok from what I can tell but does not recognize sensors from the cpu (Phenom), only the motherboard.

jmontelius, you said that some sensors from the CPU aren't being recognized. Have you tried CPU Frequency Scaling at all, and if so does it work? I'm having/had a similar problem with my new system but a different motherboard than you (Biostar T770 A2+ with an up-to-date BIOS). Have you tried updating your BIOS at all? I'm trying to figure out if this is a Linux Kernel issue or if it is a Motherboard issue. It's looking like the Kernel from what I've seen... ;\

---

### Post by jmontelius on 2008-01-31
Havn't tried to overclock it, will probably not since my intrest is mainly in programming for the cores and not how fast they run. I found this post [http://lists.lm-sensors.org/pipermail/lm-sensors/2007-December/022151.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2007-December/022151.html)  on the lm-sensors forum. So Iguess it needs some module to actually read the K10 processor.

The Asus bios is not the latest, I've got 0603 but they have 0801for download.

---

