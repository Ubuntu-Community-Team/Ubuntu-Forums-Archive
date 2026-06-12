---
title: "Understanding output of sensors."
date: 2011-06-08
forum: Desktop Environments
---

### Post by Dutchbeer on 2011-06-08
Hi all.
Need some help understanding part of the output from the command 'sensors'.
[HTML]f71882fg-isa-0a00
Adapter: ISA adapter
--
--
--
temp1:       +24.0°C  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = Intel PECI
temp2:       +57.0°C  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp3:       +30.0°C  (high = +255.0°C, hyst = +253.0°C)  
                      (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor[/HTML]
I want to know where temp1, temp2, and temp3 stand for.

---

### Post by Zorael on 2011-06-08
I don't think there's any real way of telling, besides doing educated guesses. Is this a laptop or a stationary machine?

I would guess temp2 to be the CPU die temperature. 57°C is a bit high unless the machine is under stress, but far from worryingly so. Laptops are usually warmer anyway, since there's not a whole lot of room to push air around in.

I would further guess that temp1 is the ambient case temperature, and temp3 the [northbridge chipset](http://en.wikipedia.org/wiki/Northbridge_(computing)) temperature. But if it's a laptop, temp1 (ambient case) would/should be higher, so maybe that's not it.

---

### Post by grahammechanical on 2011-06-08
Have you tried accessing the BIOS and finding out what temperatures it is measuring? A comparison of the readings might give you a clue as to which sensors are being read.

I am using xsenors and that utility labels the temperature readings. It has a nice GUI. The terminal sensors command also labels the temperature readings. And it shows a difference between high and critical readings. On your list they are both set at +255. On my system +95 is marked as critical. I do not think that the utility that you are using is working correctly.

Regards.

---

### Post by tgalati4 on 2011-06-08
What is the model of the machine?  You could do a google search on your machine model and temperature sensor and see what comes up.  You might even find pictures of where they are located.

Typically Temp1,2, and 3 are the same as what is listed in the BIOS health tab.

The high temperature (57C) could be the graphics chip (GPU).

---

### Post by Blasphemist on 2011-06-08
From what you show reported, you must have this machine way overworked (to say the least). :D

Those high numbers would melt the machine, literally. They are nearly 500 degrees Fahrenheit. Unless this is in Japan at the meltdowns, I wouldn't trust what you are using. Please do use xsensors. They are available in the software center. I use screenlets to display them. Get ready to take action at 75 degrees, maybe 80.

---

### Post by tgalati4 on 2011-06-09
The "High" and "Critical" values are not correctly set.  They would be 90C and 100C typically as most chips burn up at 110C.  They can be set in the sensors configuration file.  The hysteresis is the stickiness of the reading.  It's adds inertia to the reading to slow the response of alarms.

Here's my values for a thinkpad t43p:


tgalati4@tpad-Gloria7 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4716 RPM
temp1:       +49.0°C                                    
temp2:       +47.0°C                                    
temp3:       +36.0°C                                    
temp4:       +58.0°C                                    
temp5:       +36.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +34.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +47.0°C                                    
temp10:      +53.0°C                                    
temp11:      +48.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C                                    

You can tell that IBM had some thermal problems in the past--there are 9 discrete temperature sensors on this laptop.  You should see the fan control::shock:

---

### Post by Dutchbeer on 2011-06-09
thanks all for your input.

My machine is a workstation with:
[INDENT]MSI Eclipse (model 7520) MB,[/INDENT]
[INDENT]Intel Core i7 CPU @ 2.93 gHz max.,[/INDENT]
[INDENT]Corsair memory 6Gb.,[/INDENT]
[INDENT]3 harddrives and 2 cd-roms.[/INDENT]

Looking to the BIOS, it tells me:
CPU Temp = 23 oC, 
IOH Temp = 56
System Temp = 28
CPU fan @ 988 rpm.

xsensors:
Does not tell me which temps are measured, it only says: temp1, temp2, temp3.

Bottom line, the bios info gave me the clue.

Thanks all for your support. :p

---

### Post by Dutchbeer on 2011-06-09
> **Blasphemist said:**
> From what you show reported, you must have this machine way overworked (to say the least). :D

Those high numbers would melt the machine, literally. They are nearly 500 degrees Fahrenheit. Unless this is in Japan at the meltdowns, I wouldn't trust what you are using. Please do use xsensors. They are available in the software center. I use screenlets to display them. Get ready to take action at 75 degrees, maybe 80.

To which high numbers are you referring? The actuals look good to me or not? I believe that the high, crit and hyst reported temperatures are equipment settings. Any idea whether I can change them and, if yes how?

thx.

---

### Post by tgalati4 on 2011-06-09
You can changed the trip points in /etc/sensors.conf

Here's an example

#
##########################################################################
#### Here begins the real configuration file modified by t. galati 13 Jul 06



chip "it87-*" "it8712-*"

# The values below have been tested on Asus CUSI, CUM motherboards.

# Voltage monitors as advised in the It8705 data sheet

    label in0 "VCore 1"
    label in1 "VCore 2"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "-12V"
    label in6 "-5V"
    label in7 "Stdby"
    label in8 "VBat"

    # vid is not monitored by IT8705F
    # comment out if you have IT8712
#    ignore  vid
    ignore in5
    ignore in6 

# Incubus Saturnus reports that the IT87 chip on Asus A7V8X-X seems
# to report the VCORE voltage approximately 0.05V higher than the board's
# BIOS does. Although it doesn't make much sense physically, uncommenting
# the next line should bring the readings in line with the BIOS' ones in
# this case.
# compute in0 -0.05+@ , @+0.05

# If 3.3V reads 2X too high (Soyo Dragon and Asus A7V8X-X, for example),
# comment out following line.
#    compute in2   2*@ , @/2
#
    compute in3 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)
    compute in4 ((30/10) +1)*@  , @/((30/10) +1)
# For this family of chips the negative voltage equation is different from
# the lm78.  The chip uses two external resistor for scaling but one is
# tied to a positive reference voltage.  See ITE8705/12 datasheet (SIS950
# data sheet is wrong)
# Vs = (1 + Rin/Rf) * Vin - (Rin/Rf) * Vref.
# Vref = 4.096 volts, Vin is voltage measured, Vs is actual voltage.

# The next two are negative voltages (-12 and -5).
# The following formulas must be used. Unfortunately the datasheet
# does not give recommendations for Rin, Rf, but we can back into
# them based on a nominal +2V input to the chip, together with a 4.096V Vref.
# Formula:
#    actual V = (Vmeasured * (1 + Rin/Rf)) - (Vref * (Rin/Rf))
#    For -12V input use Rin/Rf = 6.68
#    For -5V input use Rin/Rf = 3.33
# Then you can convert the forumula to a standard form like:
#    compute in5 (7.67 * @) - 27.36  ,  (@ + 27.36) / 7.67
#    compute in6 (4.33 * @) - 13.64  ,  (@ + 13.64) / 4.33
#
# this much simpler version is reported to work for a
# Elite Group K7S5A board
#
#   compute in5 -(36/10)*@, -@/(36/10)
#   compute in6 -(56/10)*@, -@/(56/10)
#
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

    set in0_min 1.79 * 0.95
    set in0_max 1.79 * 1.05
    set in1_min 2.4
    set in1_max 2.6
    set in2_min 3.3 * 0.95
    set in2_max 3.3 * 1.05
    set in3_min 5.0 * 0.95
    set in3_max 5.0 * 1.05
    set in4_min 12 * 0.95
    set in4_max 12 * 1.05
#    set in5_max -12 * 0.95
#    set in5_min -12 * 1.05
#    set in6_max -5 * 0.95
#    set in6_min -5 * 1.05
    set in7_min 5 * 0.95
    set in7_max 5 * 1.05
    #the chip does not support in8 min/max

# Temperature
#
# Important - if your temperature readings are completely whacky
# you probably need to change the sensor type.
# Adujst and uncomment the appropriate lines below.
# The old method (modprobe it87 temp_type=0xXX) is no longer supported.
#
# 2 = thermistor; 3 = thermal diode; 0 = unused
#   set sensor1 3
#   set sensor2 3
#   set sensor3 3
# If a given sensor isn't used, you will probably want to ignore it
# (see ignore statement right below).

    label temp1       "CPU Temp"
    set   temp1_over  55
    set   temp1_low   15
    label temp2       "Motherboard"
    set   temp2_over  50
    set   temp2_low   15
   ignore temp3
#    label temp3       "Temp3"
#    set   temp3_over  45
#    set   temp3_low   15

# The A7V8X-X has temperatures inverted, and needs a conversion for
# CPU temp. Thanks to Preben Randhol for the formula.
#   label temp1       "CPU Temp"
#   label temp2       "M/B Temp"
#   compute temp1     (-15.096+1.4893*@), (@+15.096)/1.4893

# The A7V600 also has temperatures inverted, and needs a different
# conversion for CPU temp. Thanks to Dariusz Jaszkowski for the formula.
#   label temp1       "CPU Temp"
#   label temp2       "M/B Temp"
#   compute temp1     (@+128)/3, (3*@-128)

# Fans
    label fan1  "CPU Fan"
    label fan2  "Side Case Fan"
    set fan1_min 2000
    set fan2_min 3000
   ignore fan3
#    set fan3_min 3000

It's a big file so just clip out what you don't need and set sensible values.


tgalati4@tubuntu2:/etc$ sensors
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.78 V  (min =  +1.70 V, max =  +1.87 V)   
VCore 2:   +2.50 V  (min =  +2.40 V, max =  +2.61 V)   
+3.3V:     +3.34 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:       +5.03 V  (min =  +4.76 V, max =  +5.24 V)   
+12V:     +12.03 V  (min = +11.39 V, max = +12.61 V)   
Stdby:     +4.97 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:      +3.38 V
CPU Fan:  2518 RPM  (min = 2008 RPM, div = 8)          
Side Case Fan:
          4115 RPM  (min = 3013 RPM, div = 8)          
CPU Temp:    +30°C  (low  =   +15°C, high =   +55°C)   sensor = thermistor   
Motherboard:
             +31°C  (low  =   +15°C, high =   +50°C)   sensor = thermistor

My machine will beep when things get toasty, prompting my wife to say: "What is that beeping noise?"

Sometimes it's a run-away process (log files are full or can't reach a network resource) and the CPU will go to 56C then beep and I can go in to fix it.

Hysteresis is typically a few degrees and allows some sloppiness in the monitoring to filter out sudden spikes and dropouts.  You will have to research appropriate values.

---

