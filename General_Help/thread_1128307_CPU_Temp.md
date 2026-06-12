---
title: "CPU Temp"
date: 2009-04-17
forum: General Help
---

### Post by nichos on 2009-04-17
Hi, I use Ubuntu 8.10
I installed sensors as per Terminal text below, but after that I fail to locate & run whatever it is to show my CPU Temp.

I followed this instruction 
"...right click on panel >> add to panel >> hardware sensors monitor...." but " No sensors found " is added on the panel.

Considering am absolute idiot on Linux jargon, can you explain how to get this, or any other CPU Temp indication?

Thanx   ..............nick 
 
TERMINAL:-

y@y-desktop:~$ sudo apt-get install sensors-applet
[sudo] password for y: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsensors-applet-plugin0
The following NEW packages will be installed
  libsensors-applet-plugin0 sensors-applet
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 119kB of archives.
After this operation, 745kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe libsensors-applet-plugin0 2.2.1-1ubuntu4 [18.6kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe sensors-applet 2.2.1-1ubuntu4 [101kB]
Fetched 119kB in 1s (82.9kB/s)                 
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 119782 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.1-1ubuntu4_i386.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.1-1ubuntu4_i386.deb) ...
Setting up libsensors-applet-plugin0 (2.2.1-1ubuntu4) ...

Setting up sensors-applet (2.2.1-1ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

PS. could the above be not for Ubuntu 8.10???

---

### Post by toupeiro on 2009-04-17
> **nichos said:**
> Hi, I use Ubuntu 8.10
I installed sensors as per Terminal text below, but after that I fail to locate & run whatever it is to show my CPU Temp.

I followed this instruction 
"...right click on panel >> add to panel >> hardware sensors monitor...." but " No sensors found " is added on the panel.

Considering am absolute idiot on Linux jargon, can you explain how to get this, or any other CPU Temp indication?

Thanx   ..............nick 
 
TERMINAL:-

y@y-desktop:~$ sudo apt-get install sensors-applet
[sudo] password for y: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsensors-applet-plugin0
The following NEW packages will be installed
  libsensors-applet-plugin0 sensors-applet
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 119kB of archives.
After this operation, 745kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe libsensors-applet-plugin0 2.2.1-1ubuntu4 [18.6kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe sensors-applet 2.2.1-1ubuntu4 [101kB]
Fetched 119kB in 1s (82.9kB/s)                 
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 119782 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.1-1ubuntu4_i386.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.1-1ubuntu4_i386.deb) ...
Setting up libsensors-applet-plugin0 (2.2.1-1ubuntu4) ...

Setting up sensors-applet (2.2.1-1ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

PS. could the above be not for Ubuntu 8.10???

have you tried running: sudo sensors-detect

this will probe your hardware and attempt the load the proper modules into the kernel to get accurate monitoring from lmsensors.

You also might do a search in the community cafe about a program called conky, which is great for monitoring your hardware.

---

### Post by nichos on 2009-04-17
Thanx,

I did the detect & after a dozen "YES" it finished, but when I try to  add sensors on the panel it says NOT found.

Conky is not found either.

I did install previously an " X Sensors " which shows up in System Tools, but again when I add it it opens in an expandable sort of window with nothing in it.

Where do I go wrong?    ....................nick

---

### Post by balbecdaze on 2009-04-17
Have you rebooted after the dozen yes'?
Then type "sensors" into the terminal.

Do check out the conky stuff!

---

### Post by cariboo on 2009-04-17
It doesn't look like lm-sensors got installed. I don't think the applets will wotk properly with out lm-sensors.

Once you have installed lm-sensors run:

```
sudo sensors-detect
```

You have to answer yes to all the questions, pnce it has checked for sensors, it should give you a list of sensors it has found. If lm-sesnors doesn't find any sensors, your motherboard isn't supported.

Jim

---

### Post by Twitch6000 on 2009-04-17
A reboot is not needed unlike windows you only need to reboot for updates that involve xorg or kernal updates.

---

### Post by nichos on 2009-04-17
Well Done All,

did it all & Temps show in Terminal & add on Panel.

One thing though, can I make it show only CPU Temp or core 0?

Thanx again,    ..................nick

y@y-desktop:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.14 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.51 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:        +3.28 V  (min =  +0.51 V, max =  +0.00 V)   ALARM
3VCC:        +3.28 V  (min =  +0.26 V, max =  +1.02 V)   ALARM
in4:         +1.19 V  (min =  +0.00 V, max =  +0.03 V)   ALARM
in5:         +1.68 V  (min =  +0.13 V, max =  +0.00 V)   ALARM
in6:         +3.89 V  (min =  +1.64 V, max =  +3.28 V)   ALARM
VSB:         +3.28 V  (min =  +0.26 V, max =  +2.59 V)   ALARM
VBAT:        +3.23 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min = 10546 RPM, div = 128)  ALARM
Aux Fan:       0 RPM  (min = 5273 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 2636 RPM, div = 128)  ALARM
Sys Temp:    +35.0°C  (high = +75.0°C, hyst = +68.0°C)  sensor = thermistor
CPU Temp:    +27.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.300 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +26.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +31.0°C  (high = +82.0°C, crit = +100.0°C)  

[[IMG]http://img90.imageshack.us/img90/7018/screenshotepl.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshotepl.png)

---

### Post by lubosz on 2009-05-31
I also have an i7 with a DX58SO board. I had to apply this hack to sensors-detect to get my CPU detected:
[http://forums.fedoraforum.org/showthread.php?t=220570](http://forums.fedoraforum.org/showthread.php?t=220570)

You don't have to reboot after adding the lines to /etc/modules, but you can start the coretemp module if you want:

```
sudo modprobe coretemp
```

and restart lm-sensors:

```
sudo /etc/init.d/lm-sensors restart
```

check with "sensors" if it works. and after that you'd have to readd the sensors-applet to the gnome panel.

---

### Post by Amilo1718 on 2009-06-14
I don't know if it's an addition to this thread but...
my sensors are displaying:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +73.0°C  (crit = +96.0°C)                  
temp2:       +59.0°C  (crit = +85.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (crit = +100.0°C)                  

while i'm not doing a thing...
what's wrong (probably hardware) & how can i solve this?

---

