---
title: "Fan control for ECS P4M800PRO-M motherboard."
date: 2006-10-01
forum: Desktop Environments
---

### Post by cowmix on 2006-10-01
Does anyone have experience trying to get a **lmsensors** working on a motherboard that is not quite supported yet by the default package?  I have a ECS P4M800PRO-M **(IT8705F chipset)** mother boards.. I here is how far I get:

[INDENT]
[FONT="Courier New"]root@cowmyth:~# **pwmconfig**
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following PWM controls:
   9191-0290/pwm1
   9191-0290/pwm2
   9191-0290/pwm3

Found the following fan sensors:
   9191-0290/fan1_input     current speed: 2376 RPM
   9191-0290/fan2_input     current speed: 0 ... skipping!
   9191-0290/fan3_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue:

Testing pwm control 9191-0290/pwm1 ...
  9191-0290/fan1_input ... speed was 2376 now 2410
    no correlation

**No correlations were detected**.
There is either no fan connected to the output of 9191-0290/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on ... [/FONT][/INDENT]

My friend says I need this kernel module:  pca9540

Does anyone have fan control working for this motherboard under DAPPER?

---

