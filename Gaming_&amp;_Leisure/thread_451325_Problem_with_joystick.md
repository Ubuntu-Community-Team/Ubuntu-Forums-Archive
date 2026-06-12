---
title: "Problem with joystick"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by 1337 on 2007-05-22
Hello I got a problem with Joypad which I own. The joypad is connected thru Sound Blaster Live! Gameport, it has 2 axis and 8 buttons. I connected my gamepad thru gameport, I checked if the modules for SB LIve gameport are loaded with lsmod, and I loaded with modprobe both "joydev" and "analog" modules. Kernel modules detected it as:

```

[1105.204560] input: Analog 4-axis 4-button joystick as /class/input/input7

```

It is detected of course not so good, fire buttons seam to work but axises are really wrong, I used tools for calibration i.e. jscal and jscalibrator they didn't helped me too much as it was detected wrong.
I have red some documentation about Linux kernel Joystick driver: [http://www.charmed.com/txt/joystick.txt](http://www.charmed.com/txt/joystick.txt) and there is an information that there is a way to force some predefined Joypad configurations to the "analog" kernel module (section 3.1 Analog joysticks):

> 
 For other joystick types (more/less axes, hats, and buttons) support
you'll need to specify the types either on the kernel command line or on the
module command line, when inserting analog.o into the kernel. The
parameters are:

	js=type,type,type,....

  'type' is type of the joystick from the table below, defining joysticks
present on gameports in the system, starting with gameport0, second 'type'
entry defining joystick on gameport1 and so on.

	Type     | Meaning
	-----------------------------------
	none     | No analog joystick on that port
	auto     | Autodetect joystick
	2btn     | 2-button n-axis joystick
	y-joy    | Two 2-button 2-axis joysticks on an Y-cable
	y-pad    | Two 2-button 2-axis gamepads on an Y-cable
	fcs      | Thrustmaster FCS compatible joystick
	chf      | Joystick with a CH Flightstick compatible hat
	fullchf  | CH Flightstick compatible with two hats and 6 buttons
	gamepad  | 4/6-button n-axis gamepad
	gamepad8 | 8-button 2-axis gamepad  <------- this is my gamepad


There should be possibility to just do something like this:

```
sudo modprobe analog js=gamepad8
```

When I do this I got weird error:

```

FATAL: Error inserting analog (/lib/modules/2.6.20-15-generic/kernel/drivers/input/joystick/analog.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I looked into dmesg but there is not any answer to my problem. I'm using Xubuntu Feisty with all updates. Here is my question do Ubuntu kernel has modify those joystick modules or something and that's why I can use properly command line for this modules or I done something wrong? I will be grateful for any tips or information.

Thanks in advance

---

### Post by 1337 on 2007-05-22
After 2 days of work I actually worked it out I will write here for the ppl which can have the same problem a solution. I found the newest documentation file for the Joystick driver withing the Linux Kernel: [http://www.kernelhq.cc/browse-view.py?fv_nr=197138](http://www.kernelhq.cc/browse-view.py?fv_nr=197138) here is in the same Analog joysticks shown that the parameters changed **modproble analog js=XXX** gone and now is **modprobe analog map=XXX** is used atm. So if I typed** sudo modprobe map=gamepad8** my joypad were detected perfectly calibration with jscal (part of the joystick meta-package) was only needed to make it run in apps like Zsnes, pSX, ePSXe, Wine etc.

---

