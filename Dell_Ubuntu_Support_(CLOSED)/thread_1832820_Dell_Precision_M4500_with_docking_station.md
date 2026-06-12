---
title: "Dell Precision M4500 with docking station"
date: 2011-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by champost on 2011-08-25
Hi,

I have a [Dell Precision M4500]("http://www.ubuntu.com/certification/hardware/201001-5045") and would like to use it with my docking station which has a larger monitor attached to it. As of now I haven't managed to get the NVidia proprietary software to shift displays when I shut the lid of my laptop. A [related thread]("http://ubuntuforums.org/showthread.php?t=1594305") on the Ubuntu forums doesn't seem to have gone any farther...does anybody know of a solution/is experiencing similar problems ?

cheers
champost

---

### Post by JayBofMA on 2011-09-15
[FONT="Arial"]I too suffer from issues with displays when docking/undocking.  I see similar solutions ([http://ubuntuforums.org/showthread.php?t=1076486&page=6]("http://ubuntuforums.org/showthread.php?t=1076486&page=6")) that use state stored in /sys/devices/platform/dock.0/docked.  However this file does not exist for my WUBI installation of 64-Bit Natty.  I would really prefer a solution, as otherwise I am stuck with running a 32-Bit XP (don't ask...) which barely touches the power of this 8-core/8GB system.  This thing flies on Natty, but if I have to shutdown/restart every time I want to attend a meeting across the building, I will soon become dismayed.[/FONT]

---

### Post by champost on 2011-09-16
I guess I'll have to muster a good amount of courage to get into shell scripting of hardware events. I am on a native installation of Natty and still no sign of /sys/devices/platform/dock.0/docked. Though at /etc/acpi I found an undock.sh. For the record here are the contents:
```

#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

for device in /sys/devices/platform/dock.*; do
    [ -e "$device/type" ] || continue
    [ x$(cat "$device/type") = xdock_station ] || continue
    echo 1 > "$device/undock"
done

```

---

### Post by JayBofMA on 2011-09-17
Interesting.  I see that script as well.  Unfortunately it too looks for dock.* in /sys/devices/platform.  I have nothing at that location, docked or no.

On a side note, I hope they have the roads back in shape so that the peepers can keep the Green in the Green Mtn. State.

---

### Post by cntmn8td2006 on 2011-10-02
Environment: M4500 running Ubuntu 11.04 64bit.

Unfortunately, I have not been able to do what you want. I have been able to make my setup a dual monitor with the laptop screen and external monitor combined. Firstly, what drivers to use is important.

I did not use the NVIDIA proprietary driver. I used "Experimental 3D support for NVIDIA cards." Also, a fresh install of 11.04, no NVIDIA driver installed, lets you do this too.

After you have that driver, go to "Monitor Preferences" and uncheck "Same image on all monitors." You will then see the external monitor display an extension of your Ubuntu desktop. I have included an image to give you an idea of what I mean.

[IMG]http://i.imgur.com/ekyv1.png[/IMG]

---

### Post by cntmn8td2006 on 2011-10-09
Update on getting the dual monitor display to work on a docking station. 

Model Laptop: Dell M4500
Driver used: NVIDIA Accelerated Graphics Driver
OS: Ubuntu 11.04

Fire up System>Administration>NVIDIAXServerSettings

I have two monitors, LGD and DELL, and selecting the "Seperate X screen" options extends your desktop. Enabling "Enable Xinerama" now treats both monitors as a singular giant monitor. Hit apply and "Save to X Configuration File."

When you restart, Ubuntu will automatically determine if you have an available monitor to dual monitor. If not, your settings remain to a singular monitor. I haven't found a way to manually switch between single monitor and dual monitor while running the OS.

[IMG]http://i.imgur.com/4JLTg.png[/IMG]

---

### Post by MatthiasA on 2011-10-29
I use a Dell Precision M4400 with docking station and two monitors on DVI. Proprietary Nvidia drivers are in use.
Same problem here. Unplugging the Notebook results in a blank screen. When docking in, the picture is on the monitors.

Manually switching between notebook-display and dual-monitors also does not work...

Help would be much appreciated.

---

