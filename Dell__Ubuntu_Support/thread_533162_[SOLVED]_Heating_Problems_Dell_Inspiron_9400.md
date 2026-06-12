---
title: "[SOLVED] Heating Problems Dell Inspiron 9400"
date: 2007-08-23
forum: Dell  Ubuntu Support
---

### Post by Rhawi Dantas on 2007-08-23
Hi there,

I have a Dell Inspiron 9400.

I have 2 partitions one with windows xp and another one with ubuntu 7.04.

In windows the heating is controlled cos Im using NHC to undervolt my machine into 870mhz so i can keep the cpu temp at 44c. But depending on the work it can come lower.

But cos in linux i dont have nhc the temp can go up to 52c and the fans are spinning like crazy.

What could I do to use Linux without these heating problems ? Besides being irritating Im concerned with my fans that are with much more work under linunx than in windows.

Thanks to all...

---

### Post by mtbsoft on 2007-08-23
I have a 9400 too and was a little concerned about the temp too - I've seen it go up to between 50C - 60C.  That said I don't notice the fans going crazy, they seem to kick in for a minute or so when the temp gets up there and then go off - I had to put some tissue paper by the outlets and watched for movement to be sure when they were running.

Some people suggest using the i8kutils package but I couldn't get it to work on the 9400 - simply doesn't run - I'd be interested if you can.

---

### Post by Rhawi Dantas on 2007-08-24
You could try to put gkrellm to work and then loading the modules i8kutils in mine is working okay but my problem is that i dont want the computer hot like my oven :P

its really annoying cos in windows i can be for hours without any heating.

---

### Post by Rhawi Dantas on 2007-08-24
I've managed to solve the question with CPU frequency scaling.

My notebook now run much more cooler than before and without that rampants of the cooler seeking not to let my cores melt.

I've followed instructions of one post here in the community I'll sum up for this thread:

HOWTO: CPU Frequency Scaling w/ Kernel Module
I thought I would write a little howto on how to get cpu frequency scaling to work directly with the kernel modules. These modules are generally more efficient for performance computing and battery life.

Prerequisites
kernel >= 2.6.9

Step 1: Enable BIOS Support
Enter your BIOS at boot and make sure Cool'n'Quiet (AMD) or SpeedStep (Intel) is enable for you CPU. Some BIOS may not have option at all. If that is the case it is probably enabled by default. Other BIOS may have the option but it is listed as another name altogether. If that is the case check your BIOS manual for more info.

Step 2: Remove Userspace Scaling Software
powernowd
Code:

sudo apt-get remove powernowd

cpudyn
Code:

sudo apt-get remove cpudyn

Step 3: Install CPU Module
Identify your cpu type by runnig the command
Code:

cat /proc/cpuinfo

You can also Check the following links
Intel CPU Chart - [http://www.tomshardware.com/2005/11/...05/page21.html](http://www.tomshardware.com/2005/11/...05/page21.html)

AMD Sempron/Athlon/MP ( K7 )
Socket Types: A, Slot A
Code:

sudo modprobe powernow-k7

AMD Duron/Sempron/Athlon/Opteron 64 ( K8 )
Socket Types: 754, 939, 940, S1 ( 638 ), AM2 ( 940 ), F ( 1207 )
Code:

sudo modprobe powernow-k8

Intel Core Duo
Code:

sudo modprobe speedstep-centrino

Intel Pentium M
Code:

sudo modprobe speedstep-centrino

Others (Unknown) MY NOTEBOOK DELL INSPIRON 9400
I'm not entirely sure which cpus are supported using this module. If your cpu doesn't work with one of the above methods try this one.
Code:

sudo modprobe acpi-cpufreq

Step 4: Scaling Modules
Code:

sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace

Step 5: Testing/Configuration
Show Available Governors
Code:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

You should see output similar to
Code:

powersave conservative ondemand performance

conservative
Description: CPU frequency is scaled based on load in incremental steps up and down.
Code:

sudo -s
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Advanced Configuration Options
Code:

cd /sys/devices/system/cpu/cpu0/cpufreq/conservative

ondemand
Description: CPU frequency is scaled based on load.
Code:

sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Advanced Configuration Options
Code:

cd /sys/devices/system/cpu/cpu0/cpufreq/ondemand

performance
Description: CPU only runs at max frequency regardless of load.
Configuration Dir: N/A
Code:

sudo -s
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

powersave *USE THIS ONE IN THE NOTEBOOK TO SAVE THE HARDWARE*
Description: CPU only runs at min frequency regardless of load.
Configuration Dir: N/A
Code:

sudo -s
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

AND BECAUSE THE NOTEBOOK IS DUAL CORE YOU ALSO NEED TO PUT THE POWERSAVE TO THE SECOND CORE
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

Step 6: Load Modules at Boot
Add the following lines to the end of /etc/modules
Code:

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
[Module from Step 3]

Step 7: Configure Modules at Boot
This step needs to be done in order for the modules to retain your settings.
Make sure you have sysfsutils installed
Code:

sudo apt-get install sysfsutils

Then add the following lines to /etc/sysfs.conf
Code:

devices/system/cpu/cpu0/cpufreq/scaling_governor=powersave
devices/system/cpu/cpu1/cpufreq/scaling_governor=powersave

---

### Post by bimmerd00d on 2007-08-24
Rhawi, isn't it sudo apt-get install cpufreqd?

---

### Post by Rhawi Dantas on 2007-08-24
Could u point whr it would be please ?
Here it works okay...

---

### Post by mtbsoft on 2007-08-29
I did get the GKrellM/i8kutils packages to work in the end and have much better control over the fans now.

Curiously I discovered that the left fan (by the Esc key, but reported as the right fan by i8k) is far more efficient at cooling the 9400 than the right fan is.  I'd be interested to know if you find the same.

On final thing Rhawi, did you find a GUI which would enable you to select/switch the Scaling Modules on the fly?  I've had a look around but can't see anything so far.

---

### Post by Rhawi Dantas on 2007-08-29
funny yes...
i thought it was my machine

---

### Post by mtbsoft on 2007-08-29
Cool (or coolER, in your case!), I presume yours are also swapped over relative to what i8k thinks - I'll send the info. to them to update the support for our model .  I also think I might have found some manual scaling controls, now that I've posted, of course!

---

### Post by Rhawi Dantas on 2007-08-29
if you could send these manual controls for me i would be glad to get them :P

thanks anyway

---

### Post by mtbsoft on 2007-08-29
You'll probably kick yourself when you see how simple it makes it - [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html) - I didn't have to download anything.

Doesn't quite deliver all the features you have - just three CPU speeds - but does allow for selection from four scaling modes.  Ho hum!

---

