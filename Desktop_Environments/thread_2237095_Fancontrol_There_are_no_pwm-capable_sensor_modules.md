---
title: "Fancontrol: There are no pwm-capable sensor modules installed"
date: 2014-07-30
forum: Desktop Environments
---

### Post by tim59 on 2014-07-30
Hi. I don't post to forums very often, and I'm aware that there are a lot of similar thread around, but I'm very new to Linux and I'v been down a lot of dead ends today.

My problem is that my laptop is getting too hot to touch, I have recently installed Xubuntu 14.04 and the fan is no longer working. I'm trying to use an Eee PC 1015 PEM, but I'm in danger of going back to Windows!

Things I've tried:

Installed lm-sensors
Installed fancontrol
Added acpi_enforce_resources=lax to the grub file and updated

Terminal things:
I have run sudo sensors-detect which added coretemp to the modules file.
sudo modprobe coretemp, with no response but no complaint.

tim@tim-1015PEM:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +87.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +85.0°C  (crit = +100.0°C)
Core 1:       +85.0°C  (crit = +100.0°C)

tim@tim-1015PEM:~$ sudo pwmconfig
# pwmconfig revision 6166 (2013-05-01)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

I know a lot of people have had this message, but I haven't been able to resolve this. I don't know if you can tell but I'm fumbling in the dark here. Can anybody point me in a useful direction please?

I wonder if perhaps the easiest option might be to edit the fancontrol file, if anybody could give me pointers?

If I can't use this PC with PWM are there any other options to get this fan going?

NOTE: If more information would me useful, please tell me how to get it.

I thank you sincerely in advance.

Tim

---

