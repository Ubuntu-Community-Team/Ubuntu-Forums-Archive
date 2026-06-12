---
title: "Prevent usbhid from being loaded for a particular device"
date: 2009-05-31
forum: General Help
---

### Post by shabazzk on 2009-05-31
I have a IR device conntected to the USB host (#5)
```
lsusb
...
Bus 005 Device 002: ID 15c2:0043 SoundGraph Inc.
...

```

usbhid always gets loaded for this device in Jaunty 64. I want to prevent usbhid driver from being loaded for this device, which is VerndorID=15c2 and ProductID=0043.
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```
I've tried the suggested quirk:

```
/etc/modprobe.d/usbhid.conf 
options usbhid quirks=0x15c2:0x0036:0x0004

```

However, this will NOT work for Jaunty, since things have changed. I just don't know how they changed or where to look.:(

Can some one tell me how to make sure the usbhid driver does NOT get loaded for this device on Ubuntu Jaunty 64?

---

### Post by eti.que on 2009-07-01
Same issue here...

quirks just doesn't work (I have the exact same device).

Could it be caused by a modprobe.conf/modprobe.d conflict?

Does these lines ring any bell to someone?
sudo echo -n 15c2:0043 | sudo tee -a /sys/bus/usb/drivers/usbhid/unbind

or

sudo rmmod usbhid && sudo modprobe usbhid quirks=0x15c2:0x0043:0x0004

Thanks !

By the way, something a bit scary: I blacklisted usbhid. No keyboard. The imon receiver IR the proper showed that lirc_imon module was loaded.

And I was still able to move the mouse with the remote...

---

### Post by ibuclaw on 2009-07-01
Try looking into udev to see if you can prevent this.

Other than that, you you know the **actual** driver being used to communicate with the device? That would be a better thing to blacklist rather than usbhid itself...

Regards
Iain

---

### Post by eti.que on 2009-07-01
Hi Tinivole,

Thanks for the quick reply. I gave a quick look to udev and indeed there are mentions of the device, but I have no real clue on how to figure out what is the "actual driver".

It refers to some Drivers called "usb_inteface", "usb_hid", etc., as well as some "mod aliases"...

Cheers,

---

### Post by shabazzk on 2009-07-01
OK, what do you mean by taking a look at udev? I've tried to blacklist usbhid, but I guess that may be the incorrect name of the driver.

---

### Post by ibuclaw on 2009-07-01
What I mean is that if you want to ignore the device, you could probably write a udev rule for it, as udev is what handles the hotplugging of devices in Linux

ie:

```
sudo gedit /etc/udev/rules.d/10-lirc.rules
```
and put in
```
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0043", OPTIONS=="ignore_device"
```
Save, quit, then reboot your computer, and that should identify and prevent the loading of the device.

Before you do though, can you post the output of:
```
ls /dev/lirc*
ls /dev/hid*

```
incase the devices are being mounted incorrectly (it should be as lirc0 or lirc1).
If this is the case, you can alter to the above udev rule to tell udev to mount it as an lirc device.

Regards
Iain

---

### Post by shabazzk on 2009-07-03
```
$ ls /dev/lirc*
/dev/lirc0  /dev/lirc1	/dev/lircd

$ ls /dev/hid*
ls: cannot access /dev/hid*: No such file or directory
```

I did get one of the quirks to work:

```
options usbhid usbhid.quirks=0x15c2:0x0043:0x0004
```

I'm going to remove the quirk and reboot to see if usbhid occupies my lirc device, instead of the lirc driver, if not then I am going to wipe the OS and reinstall Jaunty 64, and use tinivole's method above, and post back to let you know if it worked. Thanks. It's funny, lirc comes with a rules file, but it does NOT look like that,

lirc.rules contains:
```
KERNEL=="lirc[0-9]*",	NAME="lirc/%n"

``` I thinks this is just for the dev devices that get initialized at boot, it's no wonder it didn't work for my lirc device.

------------
After removing the quirk usbhid loaded for my imon device again and the ls ouput is this:
```

$ ls /dev/hid*
/dev/hidraw0  /dev/hidraw1

$ ls /dev/lirc*
/dev/lircd

```

That worked tinivole:
```

sudo gedit /etc/udev/rules.d/10-lirc.rules
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0043", OPTIONS=="ignore_device"
```
Lirc loaded properly, without having to use a quirk:
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

How did you know to do that, and where can I read about it?

---

### Post by ibuclaw on 2009-07-04
> **shabazzk said:**
> 
That worked tinivole:
```

sudo gedit /etc/udev/rules.d/10-lirc.rules
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0043", OPTIONS=="ignore_device"
```
Lirc loaded properly, without having to use a quirk:
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

How did you know to do that, and where can I read about it?

In all honesty. That works mostly by accident. :)

And about 6 months back I learned quite a few things about udev and how to build the scripts up from scratch (pain in the backside ... but not as bad as learning LDAP).

I don't honestly have any single point of reference, but if you look around for "udev rules tutorial" you'll find what you want to know.

But just to get you started off, this command is a good starting point (might want to look into making it into a function/script):
```
udevadm info -a -p `udevadm info -q path -n /dev/**sda**`
```
The above will tell you all the available attributes udev has for potentially identifying the device /dev/sda.

Regards
Iain

---

### Post by shabazzk on 2009-07-04
OK, I guess I spoke too soon, usbhid ignores the device, and the lirc_imon gets loaded as the driver, but now I don't have lirc0 or lirc1 anymore.

When I run the commands:
```

 lsusb

Bus 003 Device 002: ID 045e:0719 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1307:0330 Transcend Information, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
and
```
dmesg | grep lirc

[   11.495965] lirc_dev: IR Remote Control driver registered, major 61 
[   11.498716] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   11.498719] lirc_imon: Venky Raju <dev@venky.ws>
[   11.498736] lirc_imon: imon_probe: found IMON device
[   11.498742] lirc_dev: lirc_register_plugin: sample_rate: 0
[   11.498786] lirc_imon: imon_probe: Registered iMON plugin(minor:0)
[   11.498813] lirc_imon: imon_probe: iMON device on usb<5:2> initialized
[   11.498822] lirc_imon: imon_probe: found IMON device
[   11.498825] lirc_dev: lirc_register_plugin: sample_rate: 0
[   11.498840] lirc_imon: imon_probe: Registered iMON plugin(minor:1)
[   11.498856] lirc_imon: imon_probe: iMON device on usb<5:2> initialized
[   11.498866] usbcore: registered new interface driver lirc_imon
```
Looks like the device gets loaded, but I'm not sure about the path too the, for example they used to be /dev/lirc0, but what are they now?

---

### Post by negora on 2010-01-25
I also have suffered from this problem and have finally "solved" it editing the /etc/rc.local file and adding a few lines:

```
modprobe -r usbhid lirc_imon
modprobe lirc_imon
modprobe usbhid
```

I know, it's a very "home-made" solution but after so much research I haven't found a reliable way of avoiding usbhid to bind my iMon before the lirc_imon module load. I've tried to fix it using udev rules, the quirks mode of the usbhid module... But no success.

---

### Post by shabazzk on 2010-01-25
Thanks, I and others came up with a somewhat better solution from this thread [http://ubuntuforums.org/showthread.php?t=1161574&page=7](http://ubuntuforums.org/showthread.php?t=1161574&page=7)
Maybe you'll like it too. Post #64 is all you have to do, but read the rest of the post if you want to understand it.
 
> **negora said:**
> I also have suffered from this problem and have finally "solved" it editing the /etc/rc.local file and adding a few lines:

```
modprobe -r usbhid lirc_imon
modprobe lirc_imon
modprobe usbhid
```

I know, it's a very "home-made" solution but after so much research I haven't found a reliable way of avoiding usbhid to bind my iMon before the lirc_imon module load. I've tried to fix it using udev rules, the quirks mode of the usbhid module... But no success.

---

### Post by negora on 2010-01-26
**shabazzk:** Yours seem to be a much more elegant solution, he he he. One day during this week I'll take a deep look to the whole thread which you mentioned. Because you're right, in my case I always need to know the "whys". Otherwise I won't be able to sleep :P .

Thanks a lot for your help, really :) .

---

