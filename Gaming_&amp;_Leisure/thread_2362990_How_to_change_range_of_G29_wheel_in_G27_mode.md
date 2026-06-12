---
title: "How to change range of G29 wheel in G27 mode?"
date: 2017-06-04
forum: Gaming &amp; Leisure
---

### Post by efflandt on 2017-06-04
Currently running up to date 64-bit Ubuntu 16.10. I thought DiRT Rally (Steam) might be easier with a racing wheel than a stubby joystick on my Logitech F710 gamepad, so I ordered a Logitech G29 Racing Wheel from Amazon. I don't have a PS3 or PS4, I just like blue better than gray of the G920. In PS3 mode the G29 works in the Windows version of DiRT Rally, but not the Linux version at this time, even though it appears to have files to support it. So in Linux I changed it to an alternate_mode as a supported G27, and that works in the game, however in G27 mode the wheel is limited to 200 degrees instead of 900 (both ranges confirmed with jstest-gtk). Force feedback works in the game, but it is somewhat twitchy with only a bit over 90 degrees to either side of center.

Modules used: hid_logitech, ff_memless (used by hid_logitech), hid (used by hid_logitech and others)

Initial lsusb for it: **Bus 002 Device 026: ID 046d:c24f Logitech, Inc.** (full 900 degree range in jstest-gtk)

lsusb after switched to G27 mode: **Bus 002 Device 027: ID 046d:c29b Logitech, Inc. G27 Racing Wheel** (200 degree range in jstest-jtk with forced feedback beyond that)

```
~$ cd /sys/devices/

/sys/devices$ find -name alternate_modes
./pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:046D:C29B.0026/alternate_modes

/sys/devices$ cat ./pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:046D:C29B.0026/alternate_modes
native: G29 Racing Wheel
DF-EX: Driving Force / Formula EX
DFP: Driving Force Pro
G25: G25 Racing Wheel
DFGT: Driving Force GT
G27: G27 Racing Wheel *
G29: G29 Racing Wheel

/sys/devices$ cat ./pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:046D:C29B.0026/range
900
```

So the range file for the wheel is still set for 900, but the wheel in G27 mode thinks it has a range of 200, which may be a default for it, but real G27 is also capable of 900 degrees.

Example of script to change the mode of a Logitech wheel:```
#!/bin/sh
# Logitech G29 as G27 Racing Wheel
cd /sys/devices
altmodes=`find -name alternate_modes`
cat $altmodes
echo please wait...
sudo bash -c "echo 'G27' > $altmodes"
sleep 6
altmodes=`find -name alternate_modes`
cat $altmodes
```Example output:```
~$ g29-g27
native: G29 Racing Wheel *
DF-EX: Driving Force / Formula EX
DFP: Driving Force Pro
G25: G25 Racing Wheel
DFGT: Driving Force GT
G27: G27 Racing Wheel
G29: G29 Racing Wheel *
please wait...
[sudo] password for efflandt: 
native: G29 Racing Wheel
DF-EX: Driving Force / Formula EX
DFP: Driving Force Pro
G25: G25 Racing Wheel
DFGT: Driving Force GT
G27: G27 Racing Wheel *
G29: G29 Racing Wheel
```Note that buttons will differ, but Dpad works in menus with button R2 to accept or L2 to go back. Keys for driving can be reassigned. The main thing is that the wheel works with forced feedback, paddle shifters work, and all 3 pedals work in the game. But when a G29 is set to G27 mode, is there some way to increase the G27 range from default 200 degrees?

---

### Post by efflandt on 2017-06-07
Apparently the range file containing 900 is ignored when switching G29 to G27 due to digital range of 0-16383 of G27 vs. 0-65535 for G29. But if the range file is changed, it spreads that 0-16383 to more degrees (bigger increments). So this is my final script to also set lock to lock range of the wheel in degrees:```
#!/bin/sh
# Logitech G29 as G27 Racing Wheel
# set range to desired lock to lock in degrees
range="540"
cd /sys/devices
altmodes=`find -name alternate_modes`
cat $altmodes
echo please wait...
sudo bash -c "echo 'G27' > $altmodes"
sleep 6
altmodes=`find -name alternate_modes`
cat $altmodes
rfile=`find -name range | grep -i c29b`
sudo bash -c "echo $range > $rfile"
echo Range has been set to $range degrees
```

---

