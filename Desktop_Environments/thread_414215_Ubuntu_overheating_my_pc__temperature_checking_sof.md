---
title: "Ubuntu overheating my pc? / temperature checking software."
date: 2007-04-19
forum: Desktop Environments
---

### Post by chiefwhosm on 2007-04-19
Hi,
Just got Feisty installed, but most of the time after a few minutes in any 3D game, the computer will shutdown saying "Critical temperature reached 89C". (i mean 89 celsius , that's just insane !)
Now tbh I have a little bit of trouble believing it because the laptop i'm on doesnt feel that hot (compared to other times when  you could have fried an egg on it).
So I wondered if there were any temperature measurement progs out there for linux (know of some for windows) and where they might be found, so I can see for myself if ubuntu really is frying my poor computer while im trying to game.
Anyone else had this problem? At some points its happened when ive been just installing games ! (and yet ive also spent my time doing apt-get installs of other stuff, no problems, it's very strange).
Never had this problem in edgy or even XP if you're wondering, that's also another reason why it's so strange :)

---

### Post by Talon2 on 2007-04-19
> **chiefwhosm said:**
> Hi,
Just got Feisty installed, but most of the time after a few minutes in any 3D game, the computer will shutdown saying "Critical temperature reached 89C". (i mean 89 celsius , that's just insane !)


Check Synaptic for a package called lm-sensors.  I'll add instructions below.  You may be able to ignor some of the instructions but I forget which ones right now.  This package does a good job...it is just a pain to set up.

Howto Install and Configure lm-sensors
========================

1. Install lm-sensors using apt-get or the Synaptic GUI.

sudo apt-get install lm-sensors


2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:

a. Copy the script file below to a text editor and save it to a file named mkdev.sh.

#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
#end of file

b. Make the file executable:

chmod 755 mkdev.sh

c. Run mkdev.sh from the current directory

sudo ./mkdev.sh


3. Now run sensors-detect and answer YES to all YES/no questions. I generally use the ISA bus rather than the SMBus bus, your choice to this question!. At the end of the detection phase, a list of modules that needs to be loaded will displayed. You will need to write these down or print the list for the next steps.

sudo sensors-detect

Below is an example of results from sensors-detect:
#************************************************* *****************************
To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----

Then, run /etc/init.d/module-init-tools

To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:

#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----
#************************************************* *******************************


4. In this example, we add the modules in reverse order (order is critical!) in "/etc/modules".

#************************************************* ***********************
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line. Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp

#For lm-sensors, i2c modules
it87
i2c-viapro
i2c-isa

#end of file!
#************************************************* ****************


4. I found that there was no "/etc/modprobe.d/local" and that "alias char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases". So, nothing to do here.


5.Now load the modules manually using modprobe and update the dependencies.

sudo modprobe i2c-sensor
sudo modprobe i2c-viapro
sudo modprobe i2c-isa
sudo modprobe it87

sudo depmod -a <may not be needed!>
sudo update-modules <may not be needed!>


6. Now test the sensor output using the lm-sensors utility "sensors".

sensors

************************************************** *****************
it87-isa-0290
Adapter: ISA adapter
VCore 1: +1.57 V (min = +1.42 V, max = +1.57 V) ALARM
VCore 2: +2.66 V (min = +2.40 V, max = +2.61 V) ALARM
+3.3V: +6.59 V (min = +3.14 V, max = +3.46 V) ALARM
+5V: +5.11 V (min = +4.76 V, max = +5.24 V)
+12V: +11.78 V (min = +11.39 V, max = +12.61 V)
-12V: -19.14 V (min = -12.63 V, max = -11.41 V) ALARM
-5V: +0.77 V (min = -5.26 V, max = -4.77 V) ALARM
Stdby: +5.00 V (min = +4.76 V, max = +5.24 V)
VBat: +3.12 V
fan1: 3668 RPM (min = 0 RPM, div =
fan2: 0 RPM (min = 664 RPM, div = ALARM
fan3: 0 RPM (min = 2657 RPM, div = 2) ALARM
M/B Temp: +39°C (low = +15°C, high = +40°C) sensor = thermistor
CPU Temp: +36°C (low = +15°C, high = +45°C) sensor = thermistor
Temp3: +96°C (low = +15°C, high = +45°C) sensor = diode
************************************************** ********************

7. Reboot Ubuntu and the sensors should now be detected during the boot process properly!

8. The sensor output may be tweaked by editing the "/etc/sensors.conf" file. It is possible to correct inacurate scaling too. For details check "man sensors.conf.

---

### Post by srt4play on 2007-04-19
Or install 'sensors-applet' in synaptic to get a nice applet in your gnome panel.

---

### Post by chiefwhosm on 2007-04-20
Well in the end I didnt install sensors (but thanks for the help anyway), when Id felt for heat before id neglected to check underneath for heat (usually when it gets hot its the side ventilation that gives off most heat and tells you you're over heating.
Anyway I've since reinstalled ubuntu, and this time noticed that restricted driver manager installed nvidia-glx (I had been trying nvidia-glx-NEW ) and so far with the old drivers, no overheating problems, so maybe a drivers bug with the glx-new caused the overheating :)

---

### Post by srt4play on 2007-04-20
If it were me, I would still install at least the sensors-applet in synaptic to keep an eye on it.  Even if you're not overheating it's still a good thing to know.

---

### Post by chiefwhosm on 2007-04-21
Oh well, i've returned to XP for now, because if it happens in XP as well then I know ive definately got a hardware problem developing, which although bad, is at least covered through my warranty :) 
Also it was wishful thinking about the older nvidia drivers, I left the computer making WINE and came back to it and found it had switched itself off :(

---

### Post by turten on 2007-04-21
Hi,

Feisty is just unusable for many people. Here are the bugs affecting false overheating.

[Bug #22336]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/22336")
[Bug #94862]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94862")

One guy is reporting 255c, I'm with 128c, you 98c. Instead of computers we have boiling pots :P:P:P

by the way.... If devs fix the bugs, how could we install a new kernel with a computer that works for a random time?? It can be one minute, five minutes, one hour....

Is there any way we can disable acpi 'CPU temperature check' in less than 1 minute??

Thanks

Editing: 
Now I can't even boot, It says 128c as CPU temp, and few seconds after reports 32c.....
It's nonsense

---

### Post by sau124 on 2007-04-21
thanks for the information..

---

### Post by turten on 2007-04-22
Well,

I'm back testing Feisty. I've upgraded my BIOS firmware and it's working for 1 hour. Maybe its not a kernel problem and it's just MY problem.....

I will continueing further testing and reporting....

---

### Post by turten on 2007-04-22
8 hours running with no problems, installed beryl, eclipse, 3D games, and lots of soft and everything works fine.

---

### Post by wconstantine on 2007-04-23
I've got artifacts all over my screen in bios and during boot of the os (vista/feisty). Is there any way to check the temp of my graphic card as easy as it was getting that sensors-applet? Can I make it see my graphic card temp aswell? The dots that I get disappear when I enter the operatives strangely enough. I only get it after running feisty tho.

---

### Post by kingkookie on 2007-04-23
Do you have a heatsink and fan on your graphics card?  Check to see if your fan is working.  I had this problem with my Nvidia 7900 GT and it turned out that the fan had stopped spinning.  Make sure all other fans are working in your PC.

---

### Post by wconstantine on 2007-04-24
Yeah the fan works fine.

---

### Post by beerorkid on 2007-04-24
I got the 128c shutdown this weekend, many times.

Kind of drove me nuts, I thought my laptop was broken.  The really strange part was that it kept happening when I was trying to install.  Live CD or text install.  it would get to the point of checking the CD and shut down.  I burned off multiple CD's and eventually got it to install with the DVD version.

---

### Post by tgalati4 on 2007-04-24
Check what's in /proc/acpi/thermal/ (your system may vary)

It could be an acpi implementation that accidently stores "128" into the thermal status thus causing an immediate shutdown.  This is probably not a real temperature.

Install lm-sensors and watch what the other sensors are doing.  You may have 2 or more to check.

Quick install (from memory--consult the forums for more extensive tutorials)

sudo apt-get install lm-sensors
sudo modprobe i2c-dev
sudo sensors-detect
answers yes to most prompts (control-C to exit if on a Thinkpad)
Copy down the results at the end
sudo modprobe (the modules suggested by the results)
sudo sensors -s (to initialize)
sensors > whyismycomputergetingsohot.txt
Right-click on the gnome-panel, add sensors-applet, now you can choose from several sensors
For KDE users, KSysguard provides similar functionality, including looking as sensors from several computers--convenient when monitoring servers over a LAN.

Good luck.

---

