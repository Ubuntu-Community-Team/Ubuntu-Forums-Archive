---
title: "need help with a conky line please"
date: 2009-03-20
forum: Desktop Environments
---

### Post by wolfe on 2009-03-20
I am trying to get my cpu temp in conky, but it does not display the right characters.  I dont understand the cut function very well, but this is what I have:

CPU Temp: ${alignr}${execi 1 sensors | grep "temp1:" | cut -d+ -f2 | cut -c2-6}C

The sensors output I am trying to draw from is:

temp1:       +23.0°C  (crit = +84.0°C)

Thanks in advance!

---

### Post by wolfe on 2009-03-20
this is the output of my 'sensors'  there are 2 temp1 lines, and I think that is confusing things

```
temp1:       +20.0°C  (crit = +84.0°C)                  

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.49 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +1.30 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +4.97 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +12.10 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +1.18 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.11 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:        +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +3.36 V
fan1:          0 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +20.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +32.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermistor
temp3:       +34.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermistor
cpu0_vid:   +0.763 V


```

---

### Post by m_duck on 2009-03-20
For just the temperature of the first "temp1:" line, the following with display it:```
${execi 1 sensors | grep -m1 "temp1:" | cut -d+ -f2 | cut -c1-7}
```The above will show ***20.0°C*** for example. To get the other temps, change the "temp1:" to "temp2:" or "temp3:".

To help perfecting it to get what you want, try running the command in the terminal and use trial and error to cut the right part. For example running the following in the terminal will give you ***temp1:       +23.0°C  (crit = +84.0°C) ***and from there you can try the different cut commands to achieve what you want:```
sensors | grep -m1 "temp1:"
```Basically, the first of the two cut commands says, find the first plus symbol and return all the characters from there to the next one. The ***-d*** switch chooses the delimeter, the plus symbol, and the ***-f 2** *chooses the second "field" separated by +'s. As you can probably tell, I am far from an expert so my explanation is a touch odd at best! So using ***-f1*** would return ***temp1:*** and using ***-f3*** would return ***84.0°C)***.

The second cut command is simpler as it just cuts characters 1 to 7 of the string produced by the grep and first cut commands.

Hopefully I've helped shed some light on it, though my explanation may have been closer to throwing a bucket of mud over it!

---

### Post by wolfe on 2009-03-20
Thanks for the input.  In a terminal

```
sensors | grep -m1 "temp1:" | cut -d+ -f2 | cut -c1-7
```

gives me exactly the output I want.  But when it is in conky, it displays as:

---

### Post by m_duck on 2009-03-21
I think that's a problem with it displaying the degrees sign. Try adding this line above "TEXT" in your .conkyrc:```
override_utf8_locale yes
```That should hopefully solve it.

---

### Post by wolfe on 2009-03-21
thanks m_duck, that resolved it!

---

