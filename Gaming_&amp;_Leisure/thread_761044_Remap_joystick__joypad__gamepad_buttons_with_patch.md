---
title: "Remap joystick / joypad / gamepad buttons with patched jscal"
date: 2008-04-20
forum: Gaming &amp; Leisure
---

### Post by landeel on 2008-04-20
[http://www.mediafire.com/?msitbdej0ad]("http://www.mediafire.com/?msitbdej0ad")
[http://ubuntuforums.org/attachment.php?attachmentid=66632&d=1208782381]("http://ubuntuforums.org/attachment.php?attachmentid=66632&d=1208782381")
This is patched version of the **jscal** utility from the **joystick** package. It will allow the remapping of buttons and axes directly into the driver.
It's compiled for Ubuntu 7.10 AMD64, but you can recompile it to any version by doing a "**make clean;make**"

I have been looking for something like this for ages. Found it here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142")

I have many joypads / joysticks with many different button layouts, and by using this utility I can reconfigure the button layout by running a simple script, intead of reconfiguring every game and emulator everytime I want to use a different joystick.
Hope you find it useful.

Quoting the patch author:
> Package: joystick
Version: 20051019-1
Severity: wishlist
Tags: patch

Motivation

I found no simple tool that would remap the joystick axes
and buttons on the device driver level (joydev module), while the driver
clearly provides the interface for this. My patch extends to
capabilities of jscal in order to remap axes and buttons. While
remapping in the X configuration file is possible, that mapping does not
seem to help in all games.


Detail

I bought a Trust GM-2550 Predator joystick the other day, and I noticed
that the axes were mapped incorrectly: the throttle in place of the
rudder, and the pinky button's axes were shifted up 1 slot in the axis
map. I found no tool to re-map the axes on the device driver (joydev)
level. While remapping is possible in the X config, this did not solve
the problem for - for example - SearchAndRescue.

Also I found no way to remap joystick buttons on the device driver
level. This is quite necessary for example for tuxkart, because some of
the buttons the game uses are unfortunately unreachable while holding
the joystick comfortably (some buttons are too far on the stick).

I found that the joydev kernel module does provide the API for axes and
button remapping. I added two command line options to jscal and two
corresponding functions that utilize the API and remap buttons and axes.
I have tested the axes and button remapping, and it works as intended. I
can swap buttons and axes as I wish.


Implementation

Please find the diff of jscal.c in joystick attached (joystick.diff).

The modified jscal.c adds two command line arguments:

-q             --print-mappings    Print the current axis and button
                                     mappings as a jscal command line

and

-u <n_of_axes,axmap1,axmap2,...,
    n_of_buttons,btnmap1,btnmap2,
    ...>       --set-mappings      Sets axis and button mappings to the
                                     specified values

An example output of -q looks like this (./jscal -q /dev/input/js0):

jscal -u
10,0,1,2,5,6,16,17,40,41,42,13,288,289,290,291,292,293,294,295,296,297,298,299,300
/dev/input/js0

The joystick has 10 axes and 13 buttons. If now one is to switch axes 2
and 5 (to get the rudder and the throttle right), one has to execute:

jscal -u
10,0,1,5,2,6,16,17,40,41,42,13,288,289,290,291,292,293,294,295,296,297,298,299,300
/dev/input/js0

changing 2,5 to 5,2 on the line.

Remapping buttons is done the same way.


---

### Post by Dark Aspect on 2008-04-20
> **landeel said:**
> [http://www.mediafire.com/?msitbdej0ad]("http://www.mediafire.com/?msitbdej0ad")
This is patched version of the **jscal** utility from the **joystick** package. It will allow the remapping of buttons and axes directly into the driver.
It's compiled for Ubuntu 7.10 AMD64, but you can recompile it to any version by doing a "**make clean;make**"

I have been looking for something like this for ages. Found it here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142")
I have many joypads / joysticks with many different button layouts, and by using this utility I can reconfigure the button layout by running a simple script, intead of reconfiguring every game and emulator everytime I want to use a different joystick.
Hope you find it useful.

Yeah Qjoypad is like this but its a little buggy,cool find I will check it out next time I am playing something.

---

### Post by landeel on 2008-04-20
Yeah, I have used qjoypad too. But I have found out the joystick response is way too slow with some games.
This solves the problem, because it works directly with the linux joystick driver.

---

### Post by grossaffe on 2008-04-21
> **landeel said:**
> Yeah, I have used qjoypad too. But I have found out the joystick response is way too slow with some games.
This solves the problem, because it works directly with the linux joystick driver.

can this map joystick axis to the mouse?

---

### Post by landeel on 2008-04-21
> can this map joystick axis to the mouse?
No. For this purpose, qjoypad is still the best solution.
jscal will only change the order of buttons and axes in the joystick node itself.

---

### Post by Dark Aspect on 2008-04-21
> **landeel said:**
> No. For this purpose, qjoypad is still the best solution.
jscal will only change the order of buttons and axes in the joystick node itself.
I never could use qjoypad's mouse feature anyway.It messed up badly and went insane when I moved the mouse axis?????

I prefer mouse and keyboard on 90% of all computer games anyway.

---

### Post by landeel on 2008-04-22
> I prefer mouse and keyboard on 90% of all computer games anyway.

Yeah, but just try playing some Street Fighter or The King of Fighters with your keyboard. :(
Qjoypad's joystick to mouse remap works perfectly for me. But I had to edit the configuration by hand, as the gui has some bugs. Try the attached configuration file.

---

### Post by Dark Aspect on 2008-04-22
> **landeel said:**
> Yeah, but just try playing some Street Fighter or The King of Fighters with your keyboard. :(
Qjoypad's joystick to mouse remap works perfectly for me. But I had to edit the configuration by hand, as the gui has some bugs. Try the attached configuration file.

Thanks,the configuration file worked :)

Don't know why it didn't work with the GUI,I guess its just buggy.I had to disable compiz cause the keyboard didn't work with the 3D desktop.

---

### Post by linuxhongkong on 2009-01-02
Thank for all of information, the jscal patch is a great solution for my EeePC 900 with Xubuntu 8.04. This is shared my experience of setting my gamepad "e-blue ZASTER" "http://www.e-blue.jp" 

power@yeung:~/download/eeepc/joy> ./jscal -q /dev/input/js0
jscal -u 6,0,1,2,3,4,40,8,288,289,290,291,292,293,294,295 /dev/input/js0

power@yeung:~/download/eeepc/joy> ./jscal -u 6,3,4,0,1,2,40,8,288,289,290,291,292,293,294,295  /dev/input/js0

power@yeung:~/download/eeepc/joy> ./jscal -q /dev/input/js0
jscal -u 6,3,4,0,1,2,40,8,288,289,290,291,292,293,294,295 /dev/input/js0

unfortunately the axis-1 is in the resverse direction. We can install the "jscalibrator" package from ubuntu 8.04. Click the "Flip" at the asix-1, calibrate, Save and reboot. Run "Jscal" at everytime of gamepad pluggin.
 
power@yeung:~/download/eeepc/joy> ./jscal -u 6,3,4,0,1,2,40,8,288,289,290,291,292,293,294,295  /dev/input/js0

Thanks

---

### Post by motin on 2009-02-24
Thanks man, great tip! This [helped me]("http://ubuntuforums.org/showthread.php?p=6791538#post6791538") get an unsupported PS2->USB adapter to work with two simple gamepads (dance mats). Cheers!

Btw for those who has 32-bit (the attached package has a compiled 64-bit version):
Unzip and run:
```

make clean
make

```
Then you have 32-bit binaries instead.

---

### Post by motin on 2009-02-27
Hmm, does this patched jscal or the even the driver itself allow switching axises with buttons? I am trying to find a solution to the [Joystick Axis Problem]("http://www.stepmania.com/wiki/Joystick_Axes_Problem")... Any ideas?

---

### Post by landeel on 2009-03-24
It's not possible as far as I know...:(

---

### Post by stimpyjcat on 2009-05-27
im trying to use a gamepad that has 2 axis but the calibrators seen 6 and x and y are used in axis 2 and 3 instead of 0 and 1 making it unable to use in most games (ie. secret maryo allow you to select the axis for movement, rRootage not)

if i try **jscal -u 6,2,3,0,1,4,5** (patched or not) got a segmentation fault and if to the last command add **,10** and 10 numbers for the buttons got a jscal: error setting button map: Invalid argument

still we have no way to remap axis? :(

ps: maybe theres an error at the JSIOCGBTNMAP value or must make a custom driver with swapped axis? :S

---

### Post by phantomcl on 2009-06-08
i have the same problem here.
Looks like jscalibrator found 6 axis, but the device have 2. generic usb pad.

Mame get the buttons ok, but de axis dont move.
Im in Ubuntu, details:
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

:~$ jscal -p /dev/input/js0
jscal -s 6,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,3,3,178956970,178956970 /dev/input/js0
~$ 


/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x79
   product : 0x11
   version : 272
   name    : "USB Gamepad "
   phys    : "usb-0000:00:1d.1-1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

---

### Post by phantomcl on 2009-06-08
LOL, readind other post, talking about lost setup usb at startup, they mencioned unplugg/replugg the usb device.

i did this and the output of js.cal -p etc/dev/js0 change:

from this:
jscal -s 6,0,0,0,0,0,0,0,0,0,0,0,0 /dev/input/

to this:
jscal -s 6,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,3,3,178956970,178956970 /dev/input/js0

And i tried mame and setup inside the game (tab) and idt worked !. ;)

So tha may help the friend who have the same problem ([stimpyjcat)]("http://ubuntuforums.org/member.php?u=404804")

i only hope that configuration not loss at reboot.

Regard !

---

### Post by landeel on 2009-06-19
Every time you unplug the device, the joystick driver will reset the configuration. I recommend creating a script, and calling it every time you want to play. You may add it to your game's shortcut.

---

### Post by landeel on 2009-06-23
Just found a very good way to load the joystick configuration automatically when you plug the device, with udev.

First you must create a udev rule. This is mine:

"/etc/udev/rules.d/85-joy-config.rules"
```

##/etc/udev/rules.d/85-joy-config.rules

##digiusb 0e8f:0013
BUS=="usb",ACTION=="add",ATTRS{idVendor}=="0e8f",ATTRS{idProduct}=="0013",RUN+="/usr/bin/joy-config-digiusb.sh"

##genesis6b 0f00:0008
BUS=="usb",ACTION=="add",ATTRS{idVendor}=="0f00",ATTRS{idProduct}=="0008",RUN+="/usr/bin/joy-config-genesis6b.sh"


```

As you can see the rule will execute the specified script when device with given idVendor and idProduct is plugged.

This is how I did the scripts:

"/usr/bin/joy-config-digiusb.sh"
```

#!/bin/bash
#digiusb 0e8f:0013
#/usr/bin/joy-config-digiusb.sh
sleep 1
jscal -u 4,0,1,16,17,10,289,290,291,293,294,295,296,297,288,292 /dev/input/js0
jscal -u 4,0,1,16,17,10,289,290,291,293,294,295,296,297,288,292 /dev/input/js1
jscal -u 4,0,1,16,17,10,289,290,291,293,294,295,296,297,288,292 /dev/input/js2
jscal -u 4,0,1,16,17,10,289,290,291,293,294,295,296,297,288,292 /dev/input/js3

```

"/usr/bin/joy-config-genesis6b.sh"
```

#!/bin/bash
#genesis6b 0f00:0008
#/usr/bin/joy-config-genesis6b.sh
sleep 1
jscal -u 2,0,1,16,309,310,311,312,313,314,308,316,317,318,319,315,304,305,306,307 /dev/input/js0
jscal -u 2,0,1,16,309,310,311,312,313,314,308,316,317,318,319,315,304,305,306,307 /dev/input/js1
jscal -u 2,0,1,16,309,310,311,312,313,314,308,316,317,318,319,315,304,305,306,307 /dev/input/js2
jscal -u 2,0,1,16,309,310,311,312,313,314,308,316,317,318,319,315,304,305,306,307 /dev/input/js3


```

I have added a "sleep 1" just in case the driver doesn't get loaded on time.

Important: don't miss the "#!/bin/bash" or it will silently fail.

Also, my scripts try to apply the layout to js0-3, as it will only succeed if the device matches the button/axis layout. I couldn't figure out a more elegant solution, but this one works for me.

---

### Post by ArmchairArmada on 2009-11-21
I remapped the axis' for my gamepad, and both -q and jstest show them remapped correctly, but when I try to play a game it's using the old axis mapping.  Does anyone know why or how to fix it?

---

