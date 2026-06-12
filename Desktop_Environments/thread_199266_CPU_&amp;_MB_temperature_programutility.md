---
title: "CPU &amp; M/B temperature program/utility"
date: 2006-06-18
forum: Desktop Environments
---

### Post by wpshooter on 2006-06-18
Is there currently a program available in either the add/remove programs section or under Synaptic program manager that will allow the checking of CPU & M/B temperatures and other system hardware information ?

Thanks.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=wpshooter]Is there currently a program available in either the add/remove programs section or under Synaptic program manager that will allow the checking of CPU & M/B temperatures and other system hardware information ?
[/QUOTE]

lm_sensors is what you want, then you can use the Gnome Sensors Applet in Gnome. I presume there is one in KDE too. However, lm_sensors doesn't configure correctly on my machine. I know it works manually as I used to have it working fine on Slackware, but I've not got round to figuring what went wrong on Ubuntu as its all new to me. CPU temp works fine, but that's it; no mobo temp or fan speed. YMMV.

---

### Post by Jason_25 on 2006-06-18
[QUOTE=wpshooter]Is there currently a program available in either the add/remove programs section or under Synaptic program manager that will allow the checking of CPU & M/B temperatures and other system hardware information ?

Thanks.[/QUOTE]
You have to install lm-sensors then run a script that comes with it that detects your sensors and loads the modules for them.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=Jason_25]You have to install lm-sensors then run a script that comes with it that detects your sensors and loads the modules for them.[/QUOTE]

Where is the script though? When I search for it, its not there;

```

root@mother:/home/luke# sensors-detect
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
root@mother:/home/luke# find / -name mkdev.sh
root@mother:/home/luke#

```

---

### Post by Jason_25 on 2006-06-18
It should be in the lm-sensors dev package.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=Jason_25]It should be in the lm-sensors dev package.[/QUOTE]

Ah thanks! I am forgetting when you download and compile from source, you usually get the dev stuff. I will try that.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=Jason_25]It should be in the lm-sensors dev package.[/QUOTE]

Can't see the dev package for lm_sensors anywhere in my Synaptic...

---

### Post by Anduu on 2006-06-18
There is a how-to on the forums for lmsensors.Do a search...

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=Anduu]There is a how-to on the forums for lmsensors.Do a search...[/QUOTE]

Yeah... for WARTY! I copied that mk-dev.sh and got it working. Don't know why that isn't included anywhere. I am coming from Slackware, and lm_sensors was a breeze there, so its slightly odd that Ubuntu which is supposed to be more user friendly doesn't include the script anywhere, in either the standard package, or the libsensers dev.

---

### Post by wpshooter on 2006-06-18
I have not had a chance to try this yet, but am I understanding correctly that if I install the Imsensor from Synaptic that it will place this application on some menu that I then can just open and give some parameters about machine and then it should correctly report info ?

Thanks.

---

### Post by jgcamp99 on 2006-06-18
wpshooter, I went thru whatever Synaptic installed when I found that lm-sensors was available. It does it's thing, but outside of a lm-sensors folder with a sensors.config.eg file in it, I can't get it to work. Maybe someone can do a step by step and be very specific for the rest of us from start to finish ? It's somewhat distrubing to see that using the Synaptic, everything else seems to install itself, but with lm-sensors, you have to go thru all this other stuff to try to get it to work ?

---

### Post by reclusivemonkey on 2006-06-19
[QUOTE=wpshooter]I have not had a chance to try this yet, but am I understanding correctly that if I install the Imsensor from Synaptic that it will place this application on some menu that I then can just open and give some parameters about machine and then it should correctly report info ?
[/QUOTE]

Not quite. LM_Sensors is a console program, you also need to run a script (as root) you will have to copy and paste from the LM_Sensors HOWTO in the Warty forum. Then you will need to run the "sensors-detect" program. If this works correctly you will then be able to run "sensors" which will give you output from all the available sensors. To get a graphical app, you will then have to add an applet in Gnome to one of your panels.

---

### Post by jgcamp99 on 2006-06-19
I'll give it a go, I started seeing sudo commands and figured it was solely done in the Ubuntu user that was created. I wasn't sure whether I had to have all the other source from lm-sensors downloads or what. Like I indicated, it seems strange that every application that I've done with Synaptic self installed smoothely from repositories, this one seems to be more involved and the fact that root is disabled by Ubuntu, this kinda defeats the purpose that sudo is the sole method that Ubuntu uses out of the box. I've re-enabled root to login thru gnome, that was one of the first things I did after the install. Citrix and a few other applications not in the repositories installed much easier as root, in fact they installed as opposed to not installing under sudo.

---

### Post by reclusivemonkey on 2006-06-19
[QUOTE=jgcamp99]Like I indicated, it seems strange that every application that I've done with Synaptic self installed smoothely from repositories, this one seems to be more involved and the fact that root is disabled by Ubuntu, this kinda defeats the purpose that sudo is the sole method that Ubuntu uses out of the box.[/QUOTE]

I'm only testing Ubuntu having come from Slackware; so far its not giving me much faith that anything can be done smoothly other than doing it yourself. Slackware 11 is calling me I think...

---

### Post by jgcamp99 on 2006-06-19
Actually this went pretty smotthly with your tips. Like I said, I saw the sudo nonsense and one of the first things I did was enable root to login in Ubuntu. My system is an MSI nf2 ultra 400 Athlon XP 3200+ K7. I had to dig deeper into the how to to do it for my particular motherboard.

I simply logged in as root, ran Synaptics Package Manager for the lm-sensors, it added a library when I did it, I trusted it to do so as I would say that it was a dependency.

After this successfully updated, lm-sensors didn't work, afterwards I had to:

follow from here in the tutorial:

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

./mkdev.sh

If you notice, I didn't use sudo, why, because I was logged in as root ! And what commands I ran was in a terminal window. And making the file, I used the text editor, both tools are in Applications, Accessories, they are the last 2 items in the drop down menu.

After this, was done, on page 2 RastaMahata posted this after his initial try failed using another sensor. I did it with both sensors, the first he indicated failed and my MSI nf2 ultra 400 took to both just the same. Funnu thing, when I sensors-detect, it tells me "no ic2 device files found, use prog//mkdev/mkdev.sh to create them.
 It works just the same though and reports back every item except fan speed(s) that the bios reports.

[http://www.ubuntuforums.org/showthread.php?t=2780&page=2&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&page=2&highlight=lm-sensors)

I got it! Just googling and reading the whole output of sensors-detect, I was able to install lm-sensors in my nforce2 chipset! Here's how I did it:

You can see here something fishy:
Code:

Probing for `Winbond W83627HF' Trying address 0x0290... Success! (confidence 8, driver `w83781d')


Anyway, I found out that w83627hf is not the right module needed for the nforce2 chipset! The right one is the driver suggested below, the w83781d.

So, here's the correct output needed:
Code:

# I2C adapter drivers 
i2c-nforce2 
i2c-nforce2 
i2c-isa 
# I2C chip drivers 
eeprom 
w83781d


copy that to /etc/modules

(hint here, etc/modules is a file not a folder that can also be edited with the text editor !)

then issue these commands:
Code:

$ modprobe i2c-isa 
$ modprobe i2c-nforce2 
$ modprobe w83781d 
$ modprobe eeprom 
$ /etc/init.d/module-init-tools 
$ update-modules

(Note: I deleted/edited out the sudo commands that were formerly in front of modprobe, I was logged in a root !)

Then just run this:
Code:

$ sensors


And it should give you something like this:
Code:

w83627hf-isa-0290 Adapter: ISA adapter VCore 1: +1.47 V (min = +1.14 V, max = +1.55 V) VCore 2: +1.54 V (min = +1.14 V, max = +1.55 V) ALARM +3.3V: +3.33 V (min = +2.82 V, max = +3.79 V) +5V: +5.05 V (min = +0.00 V, max = +0.00 V) ALARM +12V: +12.22 V (min = +0.00 V, max = +0.00 V) ALARM -12V: -12.53 V (min = -14.91 V, max = -14.91 V) ALARM -5V: -5.35 V (min = -7.71 V, max = -7.71 V) ALARM V5SB: +5.43 V (min = +0.43 V, max = +0.00 V) ALARM VBat: +3.04 V (min = +0.00 V, max = +0.00 V) ALARM fan1: 0 RPM (min = -1 RPM, div = 2) ALARM fan2: 3994 RPM (min = -1 RPM, div = 2) ALARM fan3: 0 RPM (min = 3245 RPM, div = 4) ALARM temp1: +34°C (high = +0°C, hyst = +0°C) sensor = thermistor ALARM temp2: +36.5°C (high = +53°C, hyst = +48°C) sensor = thermistor temp3: +37.0°C (high = +53°C, hyst = +48°C) sensor = thermistor vid: +1.350 V alarms: beep_enable: Sound alarm disabled eeprom-i2c-0-51 Adapter: SMBus nForce2 adapter at 5000 Memory type: DDR SDRAM DIMM Memory size (MB): 256

Anyhow. the eeprom doesn't show the memory either, but wth, I use gnome's system monitor and other gnome applets to monitor cpu usage and memory, so I 'm fat dumb and happy at the moment. Most of it works and the rpm's, from what I hear, if it doesn't show the right numbers, you have to piddle with the formulary to calculate it. At this point, a fan is a fan and with an AMD system I can hear them roaring in the cavernous Codegen 9011 mini server case that houses my maxxed out MSI Delta L w/ AXP 3200+.

With Ubuntu 6.06 LTS running this nicely, looks like Windows Vista Beta won't be getting installed anytime soon. I don't want to redo all this wonderful Linux work over Windows Vista. Gates and Microsoft have been evicted, we're looking at roughly 19 days Microsoft free and I'm happier for it !

---

### Post by jgcamp99 on 2006-06-19
BTW, I wasn't done yet. Still had to go get the gnome applet for displaying lm-sensors and that was done thru Synaptics Package Manager, just install:

sensors-applet 1.6.1-1

it's listed and goes on without a hitch, after that process, you can create the applet on the Panel, by right clicking it and using add to panel slection at the top of the drop down. If you page down you'll find an icon labeled:

Hardware Sensors Monitor

That's the sensors-applet we just installed. It's different than the System Monitor, those allow you monitor cpu usage, memory, hdd space, networking and so on.

---

