---
title: "Noob needs help with Conky temp setting"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by wilberfan on 2007-05-08
I've gotten conky working, and I think it's pretty cool...but my CPU temp constantly shows as 0 degrees centigrade. (not very helpful!)

Here is the output of "sensors"

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +31°C
Core1 Temp:
             +29°C

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.33 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +2.56 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.23 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.25 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.03 V  (min =  +0.00 V, max = +16.32 V)   
-12V:      -7.85 V  (min = -27.36 V, max =  +3.93 V)   
-5V:       -3.80 V  (min = -13.64 V, max =  +4.03 V)   
Stdby:     +2.66 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +4.08 V
fan1:     2556 RPM  (min =  664 RPM, div = 8)          
fan2:        0 RPM  (min =    0 RPM, div = 8)          
fan3:     2008 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +25°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +27°C  (low  =  +127°C, high =   +60°C)   sensor = thermistor   
Temp3:       +70°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor
```

And here is the part of my .conkyrc that applies:

```
TEXT
${color black}$nodename $sysname $kernel on $machine
${color #C0C8CD}UpTime: ${uptime}   Load: ${loadavg}
${color black}$stippled_hr
${color black}CPU Usage: $cpu  %   CPU: ${freq}mhz ${alignr}Temp: ${acpitemp}
```

Can anyone help me figure out what should go in the temp parameter(s)?  :confused:

---

### Post by jputman01 on 2007-05-08
try ```
 $ {acpitemp} .c
```

let me know if that works

---

### Post by wilberfan on 2007-05-08
> **jputman01 said:**
> try ```
 $ {acpitemp} .c
```

let me know if that works

Not at all, actually!  

The ".c" just makes things read "Temp: 0 .c"    Putting a space between the "$" and the "{" only made things worse (ie, "$ {acpitemp}" vs my existing "${acpitemp}"

:confused:

---

### Post by wilberfan on 2007-05-09
Here is some more info (that I don't really know how to interpret yet) [see attached screenshot]

How do you work out which temp (and fan) is which?    Which component are they measuring??  And do I REALLY have something that's running at 156 degrees (F)?!   And does this provide any details on how my conky settings might be changed?

---

### Post by jputman01 on 2007-05-11
> **wilberfan said:**
> Not at all, actually!  

The ".c" just makes things read "Temp: 0 .c"    Putting a space between the "$" and the "{" only made things worse (ie, "$ {acpitemp}" vs my existing "${acpitemp}"

:confused:

I wasnt meaning to put the space between "$" and "{"

---

