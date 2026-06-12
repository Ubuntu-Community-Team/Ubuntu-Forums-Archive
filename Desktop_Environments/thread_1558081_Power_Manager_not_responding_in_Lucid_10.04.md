---
title: "Power Manager not responding in Lucid 10.04"
date: 2010-08-21
forum: Desktop Environments
---

### Post by Handssolow on 2010-08-21
A dialogue box "Power Manager not responding" appears at the login screen stage though I've disabled Power Manager in System>Preferences>Startup Applications.

Also at boot up after "Ubuntu" appears the login splash screen appears but without the login dialogue box. Then follows a delay of about 50 seconds before the login dialogue box appears. After the password has been typed and entered, the Power Manger dialogue box appears for about 5 second then the normal Ubuntu desktop appears.

Background:
In the last two weeks I have made up a new desktop PC with a new Asrock DualSata mobo, new PSU, AMD Athlon 3700+ and fresh install of Lucid 10.04. I had spam in the log files from the rt2500 wifi card. This was stopped by iwconfig wlan0 power off.
[http://ubuntuforums.org/showthread.php?t=1552847](http://ubuntuforums.org/showthread.php?t=1552847)

I'm getting occasional screen freezes that may or may not be related to this power management issue. The screen dims and locks up, the USB wireless mouse still works. The graphics card is a nVidia Gefore 6610XL. Both the CPU and graphics card have worked OK in other machines without problems.

Booting up in recovery mode and I did notice that there seemed to be a delay on the line "checking battery state". But this is a Desktop PC!!!
It made no difference disabling ACPI in the bios.

---

### Post by Handssolow on 2010-08-21
I've re-read this launchpad bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)

I re-booted having first disconnected the USB transponder that communicates with the wireless keyboard and mouse and plugged in a normal keyboard and mouse. Boot up is fast without any error message coming from the power manager. I only had this one USB lead originally plugged in.
The bug looks to be a USB/Power Manager thing. 

Not really solved but hopefully a proper solution will be found soon.

---

