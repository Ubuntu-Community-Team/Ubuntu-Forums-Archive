---
title: "Speedfan works; pwmconfig doesn't.  Manual fancontrol file?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Vcount on 2006-08-17
I've been banging my head on this problem for a while now.  

I've got a computer that speedfan works on, and it is on the list of supported speedfan mobos, but pwmconfig won't work.  

I have lm-sensors installed correctly, here's my output for it:  

as99127f-i2c-0-2d
Adapter: SMBus Via Pro adapter at e800
VCore 1:   +1.70 V  (min =  +1.49 V, max =  +1.90 V)
VCore 2:   +2.56 V  (min =  +1.49 V, max =  +1.90 V)
+3.3V:     +3.44 V  (min =  +2.96 V, max =  +3.63 V)
+5V:       +4.87 V  (min =  +4.49 V, max =  +5.51 V)
+12V:     +11.98 V  (min =  +9.55 V, max = +14.41 V)
-12V:      -2.42 V  (min =  -4.07 V, max =  -0.32 V)
-5V:       -1.30 V  (min =  -1.76 V, max =  -0.82 V)
fan1:     5720 RPM  (min =   -1 RPM, div = 4)
fan2:     2860 RPM  (min =   -1 RPM, div = 4)
fan3:        0 RPM  (min = 5273 RPM, div = 4)
M/B Temp:    +30°C  (high =   +20°C, hyst =    +0°C)
CPU Temp:  +47.5°C  (high =  +100°C, hyst =   +92°C)
temp3:      -0.5°C  (high =  +122°C, hyst =  +121°C)
vid:      +1.700 V  (VRM Version 8.2)
alarms:
beep_enable:
          Sound alarm enabled

When I try to run pwmconfig, I get the " There are no pwm-capable sensor modules installed" message.  It isn't the bug, I've looked at the pwmconfig file in gedit, and line 68 is fine.  

I read where somebody else had that problem, and they manually created an /etc/fancontrol file, shown here;

INTERVAL=5
FCTEMPS= 1-0290/pwm2=1-0290/temp2_input
FCFANS= 1-0290/pwm2=1-0290/fan2_input
MINTEMP= 1-0290/pwm2=43
MAXTEMP= 1-0290/pwm2=53
MINSTART= 1-0290/pwm2=120
MINSTOP= 1-0290/pwm2=105

I've tried copying and pasting that, and get this message when I try to run fancontrol:

Enabling PWM on fans...
Starting automatic fan control...
cat: 1-0290/temp2_input: No such file or directory
Error reading temperature from /sys/bus/i2c/devices/1-0290/temp2_input
Aborting, restoring fans...
/usr/sbin/fancontrol: line 123: 1-0290/pwm2: No such file or directory
Verify fans have returned to full speed

So I am totally stumped, and don't know what I'm doing, and am being driven slowly but surely mad by the extremely loud CPU fan on this computer.  I don't understand the fancontrol file well enough to know what I'm really doing, so I'm hoping it's something really obvious like having put the wrong chipset or something that would be easily fixed.  

Is there any way to get this to work?  I'm at the point of trying to get speedfan itself to work through wine, but I'm sure there's some cleaner solution than that to the problem.

---

### Post by Bagnaj97 on 2006-08-17
I'm not sure about your problem but I know speedfan wont work through wine because it needs to install a driver to function and wine doesnt support that.

---

