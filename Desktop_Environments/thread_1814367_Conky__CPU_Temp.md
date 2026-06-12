---
title: "Conky / CPU Temp"
date: 2011-07-29
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-07-29
I am trying to use this code to add CPU temp to Conky and am getting no data . I have conky-all and lm-sensors installed . The degrees symbol C shows up , but that's all . Any thoughts on this are welcome .
```
${execi 30 sensors | grep 'Core0' | cut -c15-16}°C${color}${font}
```

---

### Post by ajgreeny on 2011-07-29
Does sensors work in terminal, and are the right sensors present in your hardware?  It never works in either of my two old machines.  Also does lm-sesnors command need to be run as root with sudo?  If so you will need to reconfigure it to be run as normal user, which I did for hddtemp (and vnstat) with ```
sudo chmod u+s /usr/sbin/hddtemp
```and ```
sudo chmod u+s /usr/bin/vnstat
```

I use a similar conky syntax to show the output of hddtemp, the nearest I can get to cpu temperature, and the only difference I can see that might be a problem is that I have a space after the **cut -c**  request:-
```
${alignc}${execi 60 hddtemp /dev/sda | cut -c 6-28} C
```
and I do not pipe twice as you do, though I can not see why these should make any difference.

---

### Post by srisharan on 2011-07-29
I use this code for CPU temp.Try if this works;

```
${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C
```

---

### Post by Frogs Hair on 2011-07-29
Thank you both for the suggestions , my other Conky themes report CPU temp .  This is the first I have put together my self and I will experiment and report back .

---

### Post by Frogs Hair on 2011-07-29
Success !  I will have to restart to get it reporting properly . Thank you again ! :D

```
   Mem: ${offset 9}$color$mem / $memmax${offset 10}
  ${color 111000}CPU 0 ${offset 9}$color${cpu cpu0}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C)   
  ${color 111000}CPU 1 ${offset 9}$color${cpu cpu1}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C) 
```

---

### Post by ajgreeny on 2011-07-30
Great!

Just to satisfy me, can you tell me how you get the degree sign to show in your conky output on screen?  If I use the degree sign from "character map" in my ~/.conkyrc file, I get a strange accented A showing, (see screenshot).

---

### Post by Frogs Hair on 2011-07-30
I used the syntax that I  posted  . I discovered that each core does not have a sensor so I eliminated one of the lines and placed the temp. below the CPU % .

---

### Post by faixan on 2011-12-12
> **Frogs Hair said:**
> Success !  I will have to restart to get it reporting properly . Thank you again ! :D

```
   Mem: ${offset 9}$color$mem / $memmax${offset 10}
  ${color 111000}CPU 0 ${offset 9}$color${cpu cpu0}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C)   
  ${color 111000}CPU 1 ${offset 9}$color${cpu cpu1}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C) 
```

Hi, i just used this code in my theme config. for conky with a few tiny changes;

here's what i used after changing the code;
```

${color FFFFFF}${font caviar dreams:size=8}Temperature CPU0: ${cpu cpu0}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)   
${color FFFFFF}${font caviar dreams:size=8}Temperature CPU1: ${cpu cpu1}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)

```
##output in attachment##
what i want to know is why the temperature values remain the same for both CPU's, does this mean i have only one sensor for both CPU's, i'm using Dell Inspiron 1545 with Core2Duo T6600 processor, also, if i change [COLOR="Red"]temp1[/COLOR] to [COLOR="Red"]temp0[/COLOR] OR [COLOR="Red"]temp2[/COLOR] as it was given, it doesn't show anything. so what's going on :confused: ?

---

### Post by faixan on 2011-12-12
also i'm trying to add fanspeeds, and the codes i've tried, just crash conky... :s any suggestions? :s

---

### Post by faixan on 2011-12-12
> **Frogs Hair said:**
> Success !  I will have to restart to get it reporting properly . Thank you again ! :D

```
   Mem: ${offset 9}$color$mem / $memmax${offset 10}
  ${color 111000}CPU 0 ${offset 9}$color${cpu cpu0}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C)   
  ${color 111000}CPU 1 ${offset 9}$color${cpu cpu1}% (${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}°C) 
```

> **faixan said:**
> Hi, i just used this code in my theme config. for conky with a few tiny changes;

here's what i used after changing the code;
```

${color FFFFFF}${font caviar dreams:size=8}Temperature CPU0: ${cpu cpu0}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)   
${color FFFFFF}${font caviar dreams:size=8}Temperature CPU1: ${cpu cpu1}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)

```
##output in attachment##
what i want to know is why the temperature values remain the same for both CPU's, does this mean i have only one sensor for both CPU's, i'm using Dell Inspiron 1545 with Core2Duo T6600 processor, also, if i change [COLOR="Red"]temp1[/COLOR] to [COLOR="Red"]temp0[/COLOR] OR [COLOR="Red"]temp2[/COLOR] as it was given, it doesn't show anything. so what's going on :confused: ?

> **faixan said:**
> also i'm trying to add fanspeeds, and the codes i've tried, just crash conky... :s any suggestions? :s

another thing, does this "sensor temp1" show the temperature from same sensor as "acpitemp" ?

---

### Post by stinkeye on 2011-12-12
> **faixan said:**
> Hi, i just used this code in my theme config. for conky with a few tiny changes;

here's what i used after changing the code;
```

${color FFFFFF}${font caviar dreams:size=8}Temperature CPU0: ${cpu cpu0}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)   
${color FFFFFF}${font caviar dreams:size=8}Temperature CPU1: ${cpu cpu1}% (${execi 8 sensors | grep -A 1 '[COLOR="Red"]temp1[/COLOR]' | cut -c13-16 | sed '/^$/d'}°C)

```
##output in attachment##
what i want to know is why the temperature values remain the same for both CPU's, does this mean i have only one sensor for both CPU's, i'm using Dell Inspiron 1545 with Core2Duo T6600 processor, also, if i change [COLOR="Red"]temp1[/COLOR] to [COLOR="Red"]temp0[/COLOR] OR [COLOR="Red"]temp2[/COLOR] as it was given, it doesn't show anything. so what's going on :confused: ?
The readings from sensors vary for different motherboards.
Post the output of ```
sensors
```
eg
```
glen@Oneiric:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +31.9°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)

it8720-isa-0228
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.23 V  
fan1:        1939 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1161 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +79.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
```

---

### Post by faixan on 2011-12-13
> **stinkeye said:**
> The readings from sensors vary for different motherboards.
Post the output of ```
sensors
```
eg
```
glen@Oneiric:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +31.9°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)

it8720-isa-0228
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.23 V  
fan1:        1939 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1161 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +79.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
```

here it is... and it explains a lot to me now... :( :( :( 

```

[10:34 AM] user@ubuntu:~ $sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.5°C  (crit = +93.0°C) 

```

but does raise another question in my mind, doesn't [color=red]hddtemp[/color]also have to be in this list? 'cause it's working in my conky config. :confused:

---

### Post by stinkeye on 2011-12-13
First try hwmon in your conky as it uses less cpu.
```
${hwmon 0 temp 1}
```



or try in the terminal
```
sensors | grep temp1 | awk '{print $2}' | cut -c2-3
```
If that works, your conky line would be...
```
${execpi [COLOR="Magenta"]5[/COLOR] sensors | [COLOR="Green"]grep temp1[/COLOR] |[COLOR="Orange"] awk '{print $2}'[/COLOR] | [COLOR="DarkOrchid"]cut -c2-3[/COLOR]}
```
[COLOR="magenta"]How often to check in secs[/COLOR]
All this line is doing is reading your sensors output, [COLOR="green"]grabbing the line with "temp1" in it[/COLOR], [COLOR="orange"]taking the second string on that line[/COLOR] (+59.5°C) and then [COLOR="darkorchid"]cutting it to the 2nd and 3rd characters[/COLOR] (ie 59)
So you can see the sensors line in conky has to be adapted according to your sensors output.


Have you configured lm_sensors yet?
[INDENT]* Run **sudo sensors-detect** and answer YES to all YES/no questions. [/INDENT]
[INDENT]* At the end of sensors-detect, a list of modules that needs to be loaded will displayed. Type "yes" to have sensors-detect insert those modules into /etc/modules[/INDENT]
[INDENT]* Reboot[/INDENT]

Once rebooted run
```
sensors
```
to see if you have more sensors info.


> but does raise another question in my mind, doesn't hddtempalso have to be in this list? 'cause it's working in my conky config.
Hard drive temp is read by hddtemp.
eg
```
hddtemp -n /dev/sda
```

---

### Post by faixan on 2011-12-14
> **stinkeye said:**
> First try hwmon in your conky as it uses less cpu.
```
${hwmon 0 temp 1}
```


it works, and it's showing me temperature 1°C more than what i am already getting by the conky config. line i'm already using, which is;
```

${execi 8 sensors | grep -A 1 'temp1' | cut -c13-16 | sed '/^$/d'}°C

```

why is that? and which one should i keep using now? ${hwmon} or ${execi} ?
> **stinkeye said:**
> 
or try in the terminal
```
sensors | grep temp1 | awk '{print $2}' | cut -c2-3
```
If that works, your conky line would be...
```
${execpi [COLOR="Magenta"]5[/COLOR] sensors | [COLOR="Green"]grep temp1[/COLOR] |[COLOR="Orange"] awk '{print $2}'[/COLOR] | [COLOR="DarkOrchid"]cut -c2-3[/COLOR]}
```

this doesn't work... there's no output in terminal for this command. :s 
> **stinkeye said:**
> 
[COLOR="magenta"]How often to check in secs[/COLOR]
All this line is doing is reading your sensors output, [COLOR="green"]grabbing the line with "temp1" in it[/COLOR], [COLOR="orange"]taking the second string on that line[/COLOR] (+59.5°C) and then [COLOR="darkorchid"]cutting it to the 2nd and 3rd characters[/COLOR] (ie 59)
So you can see the sensors line in conky has to be adapted according to your sensors output.


uderstood, thanks for explaining :)
> **stinkeye said:**
> 
Have you configured lm_sensors yet?
[INDENT]* Run **sudo sensors-detect** and answer YES to all YES/no questions. [/INDENT]
[INDENT]* At the end of sensors-detect, a list of modules that needs to be loaded will displayed. Type "yes" to have sensors-detect insert those modules into /etc/modules[/INDENT]
[INDENT]* Reboot[/INDENT]

Once rebooted run
```
sensors
```
to see if you have more sensors info.

didn't do it earlier, just ran it without inserting sensors into /etc/modules , but just did it now and here's the out put
```

[11:28 AM] user@ubuntu:~ $sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.5°C  (crit = +93.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +90.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +90.0°C, crit = +90.0°C)

```

> **stinkeye said:**
> 

Hard drive temp is read by hddtemp.
eg
```
hddtemp -n /dev/sda
```

so that means "hddtemp" is a seprate sensor... ?

---

### Post by stinkeye on 2011-12-14
```
sensors | grep temp1 | awk '{print $2}' | cut -c2-3
```
Should work as I used your sensors output.

For Core 1 and Core 2 temps you can use in terminal to check
```
sensors | grep "Core 1" | awk '{print $3}' | cut -c2-3
```
```
sensors | grep "Core 2" | awk '{print $3}' | cut -c2-3
```

and to use in conky
```
${execpi 5 sensors | grep "**Core 1**" | awk '{print $3}' | cut -c2-3}
```
```
${execpi 5 sensors | grep "**Core 2**" | awk '{print $3}' | cut -c2-3}
```

Which is the correct temp is hard to tell with sensors.
Just use the one that matches your cpu bios temp if you have one.

If you open 3 or 4 apps at the same time
eg Software centre, System Monitor and Ubuntu One 
you should see the cpu temp go up 5 or 6 degrees.

---

### Post by faixan on 2011-12-14
> **stinkeye said:**
> ```
sensors | grep temp1 | awk '{print $2}' | cut -c2-3
```
Should work as I used your sensors output.

this is working, and showing same output as the line i'm already using in my .conkyrc

> **stinkeye said:**
> 

For Core 1 and Core 2 temps you can use in terminal to check
```
sensors | grep "Core 1" | awk '{print $3}' | cut -c2-3
```

works...

> **stinkeye said:**
> 
```
sensors | grep "Core 2" | awk '{print $3}' | cut -c2-3
```

doesn't work... no output at all :( :(

---

### Post by stinkeye on 2011-12-14
My mistake shold be **core 0**
```
sensors | grep "**Core 0**" | awk '{print $3}' | cut -c2-3
```

---

### Post by faixan on 2011-12-14
> **stinkeye said:**
> My mistake shold be **core 0**
```
sensors | grep "**Core 0**" | awk '{print $3}' | cut -c2-3
```
ok, seems to be working now... lemme try it conky...

---

### Post by faixan on 2011-12-15
> **stinkeye said:**
> My mistake shold be **core 0**
```
sensors | grep "**Core 0**" | awk '{print $3}' | cut -c2-3
```

here're the lines in my .conkyrc

```

${color FFFFFF}${font caviar dreams:size=8}CPU Temperature: ${execi 8 sensors | grep -A 1 'temp1' | cut -c13-16 | sed '/^$/d'}°C
${color FFFFFF}${font caviar dreams:size=8}HWMON TEMP: ${hwmon 0 temp 1}
${color FFFFFF}${font caviar dreams:size=8}CPU-Core 0 Temperature: ${execpi 5 | sensors | grep "Core 0" | awk '{print $3}' | cut -c2-3}°C
${color FFFFFF}${font caviar dreams:size=8}CPU-Core 1 Temperature: ${execpi 5 | sensors | grep "Core 1" | awk '{print $3}' | cut -c2-3}°C
${color FFFFFF}${font caviar dreams:size=8}${exec hddname.sh sda}HDD Temperature: +${hddtemp /dev/sda}°C

```

and their output is in attachment :confused:

---

### Post by stinkeye on 2011-12-15
> **faixan said:**
> here're the lines in my .conkyrc

```

${color FFFFFF}${font caviar dreams:size=8}CPU Temperature: ${execi 8 sensors | grep -A 1 'temp1' | cut -c13-16 | sed '/^$/d'}°C
${color FFFFFF}${font caviar dreams:size=8}HWMON TEMP: ${hwmon 0 temp 1}
${color FFFFFF}${font caviar dreams:size=8}CPU-Core 0 Temperature: ${execpi 5 | sensors | grep "Core 0" | awk '{print $3}' | cut -c2-3}°C
${color FFFFFF}${font caviar dreams:size=8}CPU-Core 1 Temperature: ${execpi 5 | sensors | grep "Core 1" | awk '{print $3}' | cut -c2-3}°C
${color FFFFFF}${font caviar dreams:size=8}${exec hddname.sh sda}HDD Temperature: +${hddtemp /dev/sda}°C

```

and their output is in attachment :confused:

Another mistake by me.There is no pipe between execpi and sensors
```
${execpi 5 | sensors
```
should be
```
${execpi 5 sensors
```

---

### Post by faixan on 2011-12-15
> **stinkeye said:**
> Another mistake by me.There is no pipe between execpi and sensors
```
${execpi 5 | sensors
```
should be
```
${execpi 5 sensors
```

working like a charm now :) thanks, just one last thing, i'm still not clear about why there's the difference between "hwmon temp1" and "cpu temp"

does temp1 refers to some different hardware temp?

---

### Post by stinkeye on 2011-12-15
> **faixan said:**
> working like a charm now :) thanks, just one last thing, i'm still not clear about why there's the difference between "hwmon temp1" and "cpu temp"

does temp1 refers to some different hardware temp?
hwmon temps are from sensors.

See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11013044&postcount=18302") for more info.

---

### Post by faixan on 2011-12-15
> **stinkeye said:**
> hwmon temps are from sensors.

See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11013044&postcount=18302") for more info.

Thanks :) :)

---

### Post by jaws222 on 2012-10-14
> **faixan said:**
> this is working, and showing same output as the line i'm already using in my .conkyrc


works...


doesn't work... no output at all :( :(

5 sensors | grep temp1 | awk '{print $2}' | cut -c2-3}

Above worked for me.  Awesome!!  Thank You!!

---

### Post by wildmanne39 on 2012-10-14
Old thread closed.

---

