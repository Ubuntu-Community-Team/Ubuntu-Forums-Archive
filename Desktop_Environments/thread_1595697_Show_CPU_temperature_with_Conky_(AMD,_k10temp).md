---
title: "Show CPU temperature with Conky (AMD, k10temp)"
date: 2010-10-13
forum: Desktop Environments
---

### Post by Sunships on 2010-10-13
Hello,

I'm struggling to get my Conky feed to show the CPU temperature. I'm working with a fresh install of Ubuntu 10.10. Currently my Conky display shows a CPU temperature of 0 degrees Celsius, and I know this isn't true because I built the computer myself and I'm definitely not that good! Also, the GNOME hardware applet contradicts this and gives a more realistic CPU temperature of 33 degrees Celsius. Any ideas on what I can do to rectify this and get this displayed in my Conky? 

Thanks!

The science bit:

I have done a sudo-sensors detect, and for CPU sensors it tells me:

```
Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No
```

The end summary is as follows:
```

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)
```

and here is the relevant snippet of my conkymain file:

```
${color purple}CPU ${hr 4}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

```

---

### Post by Sunships on 2010-10-13
*bump*

---

### Post by nilarimogard on 2010-10-14
Restart your computer and it should work.

---

### Post by Sunships on 2010-10-14
Hello, I am afraid it still does not work.

---

### Post by Sunships on 2010-10-14
*bump*

---

### Post by sendblink23 on 2010-10-14
Trust me its a real pain.. I simply gave up for it to recognize all my temps sensorings/monitoring of everything

I simply decided to just use: sensors   
since it does display my cpu core temp and it was the only thing I honestly really cared about

Then on Cocky I would simply use this line for it to be visible:
```
${execi 8 sensors | grep -A 1 'temp1' | cut -c13-16 | sed '/^$/d'}C

```
Ofcourse use this only if sensors is showing your cpu core temp

---

### Post by Sunships on 2010-10-15
> **sendblink23 said:**
> Trust me its a real pain.. I simply gave up for it to recognize all my temps sensorings/monitoring of everything

I simply decided to just use: sensors   
since it does display my cpu core temp and it was the only thing I honestly really cared about

Then on Cocky I would simply use this line for it to be visible:
```
${execi 8 sensors | grep -A 1 'temp1' | cut -c13-16 | sed '/^$/d'}C

```
Ofcourse use this only if sensors is showing your cpu core temp

This worked, thank you :)

---

### Post by stratoka on 2010-10-17
worked for me too.i just cshneged the temp1 to temp 2 becouse thats my cpu temp:D

---

### Post by embain14 on 2010-12-08
Awesome worked great thank you

---

### Post by fernandoch on 2010-12-23
How can you tell which one is the CPU temp? Temp1 or temp2?

---

### Post by dolmance41 on 2011-11-27
Module cpuid loaded successfully. Silicon Integrated Systems SIS5595...                       No VIA VT82C686 Integrated Sensors...                          No VIA VT8231 Integrated Sensors...                            No AMD K8 thermal sensors...                                   No AMD Family 10h thermal sensors...                           No AMD Family 11h thermal sensors...                           Success!     (driver `k10temp') AMD Family 12h and 14h thermal sensors...                   No Intel digital thermal sensor...                             No Intel AMB FB-DIMM thermal sensor...                         No VIA C7 thermal sensor...                                    No VIA Nano thermal sensor...                                  No   this is my output and that solution you posted DOES NOT WORK!!!! please tell me how i can get my temp to display without + signs and .0 before the temp!!!!!!!

---

