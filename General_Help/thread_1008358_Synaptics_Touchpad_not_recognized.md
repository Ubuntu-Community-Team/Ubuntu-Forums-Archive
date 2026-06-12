---
title: "Synaptics Touchpad not recognized"
date: 2008-12-11
forum: General Help
---

### Post by unihiekka on 2008-12-11
Hi,

I have just compiled my own custom kernel based on the 2.6.27.7 vanilla, which all went fine. My boot up process has reduced by 10 seconds and I believe I can bite off another 5-8 seconds if I wanted to, but so far I have a problem. My NEC Versa P520 laptop has a Synaptics Touchpad that works fine in my current Ubuntu 7.10 with the standard 2.6.22-16 kernel. However, on my own kernel it somehow does not seem to be recognized. I don't believe that there is a problem with the supplied driver or even with the kernel. I guess there is a problem with Xorg or Ubuntu, but I have no idea what it is.

Here's my dmesg (shortened):

```
Linux version 2.6.27.7-sigma (root@teletraan) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Dec 7 14:13:57 EET 2008
[...]
PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice

```

And of course my /proc/bus/input/devices:

```
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7
```

which shows that it's not found (in the new system). My Xorg.0.log tells me that

```
Synaptics Touchpad no synaptics event device found (checked 15 nodes)
Query no Synaptics: 6003C8
[...] no touchpad detected and no repeater device
unable to query/initialize Synaptics hardware
```

but in my kernel evdev is built in, so that's it's not missing. Making it a module does not resolve the problem.

Somehow there are no /dev/input/event* entries, which are normally found according to my working Xorg log: "Synaptics Touchpad auto-dev sets device to /dev/input/event*" etc.

I don't know why my system does not recognize my touchpad with the new kernel. Any thoughts? I have tried using a linux-source (downloaded with aptitude) but that one has the same problem, even if I use my old configuration.

Actually, I had the same problem with the live cd of 8.1, which is why I am still with 7.1.

Anyone have a solution or idea what's wrong/missing?

---

### Post by Titan8990 on 2008-12-11
I have a feeling this is not going to work but its worth a shot:


sudo dpkg-reconfigure xserver-xorg


When you get to input selection, select /dev/input/mouse (should be the top entry). That works for my touchpad.

---

### Post by unihiekka on 2008-12-12
Yes, you are right: it does not work. Any other ideas?

---

### Post by unihiekka on 2008-12-13
And something along the lines of [this]("http://ubuntuforums.org/showthread.php?t=493758") does not work, by the way. Any thoughts, people?

---

### Post by unihiekka on 2008-12-19
*bump*

---

### Post by Titan8990 on 2008-12-19
Based on the fact that you compiled your own Vanilla kernel I am guessing you don't have a needed module to control /dev/input/mouse.

Most Ubuntu members don't compile their kernels so it might be difficult for you to find help with that particular issue.

---

