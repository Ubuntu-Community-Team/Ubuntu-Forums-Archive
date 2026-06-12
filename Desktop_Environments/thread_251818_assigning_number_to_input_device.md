---
title: "assigning number to input device"
date: 2006-09-05
forum: Desktop Environments
---

### Post by rkvj on 2006-09-05
Hello,

I'm using 32-bit version of Ubuntu with AMD64 3000+ processor and am having trouble getting the IR remote that came with my TV capture card, to work. The capture card/remote "just works" and I use lirc with the following options in /etc/hardware.conf:

LIRCD_ARGS="-H dev/input -d /dev/input/event3"
MODULES="ir_kbd_i2c evdev"


I also changed the lircrc file to suit my needs and everything worked until the next reboot. The remote doesn't work on rebooting consistently, which I think is because lirc assumes '/dev/input/event1' to be the remote controller, but the input device number (/dev/input/eventX) changes each time I restart the computer. Is there a way to assign the device numbers to each of the input devices so that its consistent?

Here's the output of 'cat /proc/bus/input/devices':

---------------------------------------------------------
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6

I: Bus=0001 Vendor=1461 Product=f31f Version=0001
N: Name="saa7134 IR (Avermedia AVerTV GO"
P: Phys=pci-0000:02:00.0/ir0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=100003
B: KEY=40fc310 82140000 0 0 0 0 2048000 180 4001 9e0000 7bb80 0 0

I: Bus=0003 Vendor=046d Product=c505 Version=1721
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.2-4.1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c505 Version=1721
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.2-4.1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=103

----------------------------------------------------------

Thanks

--RKVJ

---

