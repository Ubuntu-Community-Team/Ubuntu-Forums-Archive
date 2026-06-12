---
title: "lm-sensors in gdesklets"
date: 2009-03-16
forum: General Help
---

### Post by jamesclayden on 2009-03-16
i have tried to add the desklets for lm-sensors but they don't work even though lm-sensors is working perfectly. when i try to configure desklet nothing happens.

does anyone have a lm-sensors desklet that works?

---

### Post by DeMus on 2009-03-16
> **jamesclayden said:**
> i have tried to add the desklets for lm-sensors but they don't work even though lm-sensors is working perfectly. when i try to configure desklet nothing happens.

does anyone have a lm-sensors desklet that works?

It's a long story, but I have used it a couple of times and it works. It's not mine, I tell you that, so if you get problems, don't blame me. For me it works.

**Howto Install and Configure lm-sensors**
========================

1. Install lm-sensors using apt-get or the Synaptic GUI.

```
sudo apt-get install lm-sensors
```


2. Run the mkdev.sh script in the lm-sensors source. It is extracted below:

a. Copy the script file below to a text editor and save it to a file named mkdev.sh.

```
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
```

b. Make the file executable:

```
chmod 755 mkdev.sh
```

c. Run mkdev.sh from the current directory

```
sudo ./mkdev.sh
```


3. Now run sensors-detect and answer YES to all YES/no questions. I generally use the ISA bus rather than the SMBus bus, your choice to this question!. At the end of the detection phase, a list of modules that needs to be loaded will displayed. You will need to write these down or print the list for the next steps.

```
sudo sensors-detect
```

Below is an example of results from sensors-detect:
#************************************************* *****************************
To make the sensors modules behave correctly, add these lines to
/etc/modules:

```
#----cut here----
# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----
```

Then, run
```
sudo /etc/init.d/module-init-tools
```

To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:

```
#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----
#************************************************* *******************************
```


4. In this example, we add the modules in reverse order (order is critical!) in "/etc/modules".

```
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

```

4. I found that there was no "/etc/modprobe.d/local" and that "alias char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases". So, nothing to do here.


5.Now load the modules manually using modprobe and update the dependencies.

```
sudo modprobe i2c-sensor
sudo modprobe i2c-viapro
sudo modprobe i2c-isa
sudo modprobe it87

sudo depmod -a <may not be needed!>
sudo update-modules <may not be needed!>
```


6. Now test the sensor output using the lm-sensors utility "sensors".

```
sensors

```
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
fan2: 0 RPM (min = 664 RPM, div =             ALARM
fan3: 0 RPM (min = 2657 RPM, div = 2) ALARM
M/B Temp: +39°C (low = +15°C, high = +40°C) sensor = thermistor
CPU Temp: +36°C (low = +15°C, high = +45°C) sensor = thermistor
Temp3: +96°C (low = +15°C, high = +45°C) sensor = diode
************************************************** ********************

7. **Reboot** Ubuntu and the sensors should now be detected during the boot process properly!

8. The sensor output may be tweaked by editing the "/etc/sensors.conf" file. It is possible to correct inaccurate scaling too. For details check "man sensors.conf.

Once you have lm-sensors installed, you should have a readout with 'sensors'

Notice that my CPU fan is running really slowly, only 1100 RPM. The CPU temp is a little high, so I need to do some tweaking of the config there. The fan can run so slowly and quietly, because it's a large 12 cm fan made by Zalman (it's the 7000B AlCu). If your output does not display an RPM for your CPU fan, and you are positive it is running, you need to increase the fan divisor. If your fan speed is shown and higher than 0, skip the next step.

Increasing fan_div
The first line of the sensors output is the chipset your motherboard uses to read the speeds/temps/voltages. Make a backup first:
Code:
```
$ sudo cp /etc/sensors.conf /etc/sensors.conf_original
```
Edit the /etc/sensors.conf file as root
Code:
```
$ sudo gedit /etc/sensors.conf
```
and look up your exact chipset. The names all look alike, so make sure the one you are editing is yours. Add the line fanX_div 4 near the start of your chipset config. Replace the X with the number of your CPU fan's, for me that was 2. You have to figure out for yourself which one it is, but it's probably 1, 2 or 3.

Save, and run 
Code:
```
$ sudo sensors -s
```
which will reload the sensors.conf's set variables.
Run sensors again and check if there is an RPM readout. If not, increase the divisor to 8, 16 or 32. YMMV!

Here is a sample from my sensors.conf
Code:
chip "w83627thf-*" "w83637hf-*"

    label in0 "VCore"
    label in1 "+12V"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "-12V"
    label in7 "V5SB"
    label in8 "VBat"

    compute in1 ((28/10)+1)*@, @/((28/10)+1)
    compute in3 ((34/51)+1)*@, @/((34/51)+1)
    compute in4 (5.14*@)-14.91, (@+14.91)/5.14
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

    set fan2_div 8

    <snip>
You can safely ignore anything that's not fanX_div. I would advise you to leave the other default settings as they are.


If you like to see (some of) the sensors, you can add a small program to your panel: Sensors Applet.
You can install it through Synaptic. Look for Sensors-applet.
After installation and a reboot you can add it to your panel and through it's preferences you can choose which sensors you look to see.
Have fun with it.

---

