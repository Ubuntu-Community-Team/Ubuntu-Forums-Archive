---
title: "Monotoring CPU and/or GPU temerature - ubuntu 7.04"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by SpinningAround on 2007-09-28
Hi

I'm quite new to ubuntu, but have used linux for some short periods before, since i like to see the temprature at my CPU and GPU am'i currently looking for a program or similar that can do this in linux, In windows do these usally come with the product or can be downloaded. 

I found a solution to the temp with the GPU but since I'm using the restricted device manager did I get nvidia-glx and (think) I see the temp since if I install nvidia-config or similar will this cause nvidia-glx to be uninstalled. Is there a possible work around?

Graficcard: Nvidia Geforce 6600

To the CPU that I think will be a little harder, in windows did I use the program CoreCenter, I unsure if there is a program that is doing a similar job with monitoring the CPU/system temp.

The moderboard is MSI K8N Neo4

---

### Post by fedex1993 on 2007-09-28
There are some are you good with coding like you know a little bit of coding or do you want something that you can edit with a gui. I personaly use Conky its a nice little bar that sits on teh side of your screen ro you can choose where you want to put it at. The only problem with customizing conky is done all with commands instead of a gui. There is also gkrellm its has a gui you can edit with but there are less features so do what you want and what you like.

---

### Post by hyperair on 2007-09-29
I use Conky too, but you need to set up lm-sensors first to detect fan speed and CPU temperature.

Install lm-sensors
```

sudo apt-get install lm-sensors

```

Set up lm-sensors (Press enter all the way for all the questions asked)
```

sudo sensors-detect

```

The last few lines of your output should look like this:
```

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# Chip drivers
it87
#----cut here----

```

Load all the required modules (repeat this action replacing it87 with whatever modules you have there:
```

sudo modprobe it87

```

Open your /etc/modules file and add it in:
```

sudo gedit /etc/modules

```

Test your lm-sensors output:
```

sensors

```

You should get something like:
```

it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.55 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
VCore 2:   +1.63 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:     +3.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+5V:       +5.05 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+12V:      +0.00 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
-12V:     -27.36 V  (min = -27.36 V, max = -27.36 V)   ALARM
-5V:      -13.64 V  (min = -13.64 V, max = -13.64 V)   ALARM
Stdby:     +0.00 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
VBat:      +4.08 V
fan1:     2947 RPM  (min =    0 RPM, div = 2)          
fan2:        0 RPM  (min =    0 RPM, div = 2)          
fan3:        0 RPM  (min =    0 RPM, div = 2)          
M/B Temp:    +41°C  (low  =    +0°C, high =    +0°C)   sensor = diode   
CPU Temp:   +127°C  (low  =   +70°C, high =   +80°C)   sensor = thermistor   
Temp3:      +127°C  (low  =    +0°C, high =    +0°C)   sensor = thermistor   

```
Something to note: I've read that the modules detected by sensors-detect have to be entered into /etc/modules in reverse order, so if it lists a,b,c you have to add it into /etc/modules as c,b,a. I haven't noticed the need for it.

After that you should have no problem getting a program like gkrellm to show you the CPU temperature.

p.s. my voltages seem a lil off for some reason though.

---

### Post by SpinningAround on 2007-09-30
EDIT:

sudo modprobe fixed it :)

PS. Thanks for the help

---

