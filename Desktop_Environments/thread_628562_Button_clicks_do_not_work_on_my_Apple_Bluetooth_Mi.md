---
title: "Button clicks do not work on my Apple Bluetooth Mighty Mouse"
date: 2007-12-01
forum: Desktop Environments
---

### Post by salimfadhley on 2007-12-01
I've recently installed an Apple Mighty Mouse - at first it worked fine, but after a system reset I now find that I can move the mouse-pointer but button mouse-clicks have no effect. Strangely the scroll-wheel works fine and I can scroll windows, however not being able to click means I cannot select anything. 

I'm pretty sure that this is not an X configuration issue - if it was I'd expect only some of the buttons to work (e.g. just the main one), however the issue is that movement works but clicks do not.

Any suggestions?

Thanks

---

### Post by Monkey_Man on 2007-12-14
I have the same problem with my mighty mouse. Although the clicks on mine have never worked. I was wondering if you found a solution or if anyone else has some idea how to solve this?

---

### Post by zoomitdude on 2007-12-23
Same problem here mouse pairs as follows:
@beecat:~$ uname -r
2.6.22-14-generic

Ubuntu 7.10

mouse is: Model A1197

Using bluetooth tutorial from [http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

ubuntu:~$ hcitool scan

sudo gedit /etc/bluetooth/hcid.conf

device xx:xx:xx:xx:xx:xx {
    name "Mighty Mouse"
    auth enable;
    encrypt enable;
}

sudo /etc/init.d/bluetooth restart

sudo hidd --connect xx:xx:xx:xx:xx:xx

pin is 0000

pairs fine, can move pointer about, scroll ball works up/down fine in firefox but no clicks :-(

cat /proc/bus/input/devices
I: Bus=0005 Vendor=05ac Product=030c Version=0200
N: Name="Apple Computer, Inc. Mighty Mouse"
P: Phys=xx:xx:xx:xx:xx:xx
S: Sysfs=/class/input/input10
U: Uniq=xx:xx:xx:xx:xx:xx
H: Handlers=mouse3 event9 
B: EV=100007
B: KEY=f0000 0 0 0 0 0 0 0 0
B: REL=143

running  sudo hcidump
moving the mouse as well as moving the scroll ball generates packets but clicking buttons does not :-( so this is a bug between bluetooth and the mouse.

Using a bluetooth micro$oft Intellimouse until i can find a solution that works.... :-(

Tried an apple usb mouse type A1152 works perfectly.. hurmmm

---

### Post by zoomitdude on 2007-12-24
Problem Solved!
[http://blog.heatxsink.com/archives/linux/](http://blog.heatxsink.com/archives/linux/)

followed his walk though Apple wireless Mighty Mouse on Ubuntu Dapper

Why:
I had messed about with my  hcid.conf file previously

sudo gedit /etc/bluetooth/hcid.conf

```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0000";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm none;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

device xx:xx:xx:xx:xx:xx {
    name "Apple Wireless Keyboard";
    auth enable;
    encrypt enable;
}

device xx:xx:xx:xx:xx:xx {
    name "Mighty Mouse"
    auth enable;
    encrypt enable;
}

```

sudo /etc/init.d/bluetooth restart

my mouse started clicking away!

There is no comparison between the apple mouse and the bluetooth micro$oft Intellimouse explorer. Apple wins hands down for multi surface use and responsiveness. 

Three Mouse buttons + scroll ball work nicely too, thank you ubuntu!

---

