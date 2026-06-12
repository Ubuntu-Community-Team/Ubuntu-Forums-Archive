---
title: "XBox 360 Controller issues - no /dev/input/js0"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by kalin.au on 2007-05-23
Hi, I've been trying to configure a USB XBox 360 controller. So far I have compiled and installed the xpad.ko module, and modprobe'd it to add it to the kernel.

Everything seems to be ok except that there is no /dev/input/js0 coming up for the device.

```

kalin@barn:~ $ modprobe -l | grep xpad
/lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/xpad.ko

```
The module seems to be installed and running.

```

kalin@barn:~ $ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 017: ID 045e:028e Microsoft Corp. 
Bus 001 Device 016: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 011: ID 046d:c222 Logitech, Inc. 
Bus 001 Device 008: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 010: ID 046d:c221 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```
The device appears to be present here.

```

$ udevinfo -q all -a -p /class/input/input7 | tee udev-output.txt

```
Going through devices with this udevinfo command shows that:

/class/input/input6   -- Logitech Gaming Keyboard
/class/input/input7   -- Logitech Gaming Keyboard
/class/input/input8   -- G15 Keyboard
/class/input/input9   -- PC Speaker
/class/input/input10  -- Power Button
/class/input/input11  -- Power Button
/class/input/input12  -- Logitech USB Gaming Mouse

I'm not sure if one of these devices is using up some input slot that is required for the controller or something. I don't really understand udevinfo.

```

kalin@barn:~ $ cat /proc/bus/usb/devices 
...
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 17 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=028e Rev= 1.10
S:  Manufacturer=&#65533;Microsoft Corporation
S:  Product=Controller
S:  SerialNumber=0237905
C:* #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=5d Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=4ms
E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=8ms
I:  If#= 1 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=5d Prot=03 Driver=(none)
E:  Ad=83(I) Atr=03(Int.) MxPS=  32 Ivl=2ms
E:  Ad=04(O) Atr=03(Int.) MxPS=  32 Ivl=4ms
E:  Ad=85(I) Atr=03(Int.) MxPS=  32 Ivl=64ms
E:  Ad=05(O) Atr=03(Int.) MxPS=  32 Ivl=16ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=5d Prot=02 Driver=(none)
E:  Ad=86(I) Atr=03(Int.) MxPS=  32 Ivl=16ms
I:  If#= 3 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=fd Prot=13 Driver=(none)
...

```
Looks like the device is listed here as well, which appears to be the list of currently active devices.


Now, when I plug the controller in, the light turns on and flashes a few times (sequence of long, short, short), then turns off.
```

kalin@barn:~ $ cat /var/log/messages
May 23 23:52:54 barn kernel: [ 2363.476000] usb 1-2: new full speed USB device using ohci_hcd and address 17
May 23 23:52:54 barn kernel: [ 2363.696000] usb 1-2: configuration #1 chosen from 1 choice

```
(udevinfo for /class/input/input17 was empty after this)
It looks like this is missing the detection of the actual device type, I think it should be something like this:


Snipped from [http://ubuntuforums.org/showthread.php?t=404577&page=3](http://ubuntuforums.org/showthread.php?t=404577&page=3) :
> 
May 5 16:27:31 Mercury kernel: [ 150.713656] usb 2-4: new full speed USB device using ohci_hcd and address 4
May 5 16:27:31 Mercury kernel: [ 150.930603] usb 2-4: configuration #1 chosen from 1 choice
May 5 16:27:31 Mercury kernel: [ 150.968765] input: Microsoft Xbox 360 Controller as /class/input/input7

but for some reason the last line is not showing up.

The last thing I could find to try was using mknod to create the device node manually.

```

kalin@barn:~ $ mknod /dev/input/js0 c 13 0
kalin@barn:~ $ cat /dev/input/js0
cat: /dev/input/js0: No such device

```

So, that's the collection of every help thread and installation guide tips and info that I could collect, and every piece of information that I could find that could be relevant.

I'm totally out of ideas. Anyone know what might be going on here?

---

### Post by po0f on 2007-05-23
kalin.au,

Which version kernel are you running?  Post the output of:

```
$ uname -r
```

if you would, please.

---

### Post by kalin.au on 2007-05-23
```

kalin@barn:~ $ uname -r
2.6.20-15-generic

```
Compilation of the xpad module was done with the uname'd headers, so afaict there should be no mismatch there.

---

### Post by sandy_freelance on 2008-10-01
Hi,

I also have the 'no /dev/input/js0' problem.  I am running 2.6.18-4-486 with xpad360 loading fine:

   /usr/src/modules/xpad360/xpad.c: X-Box pad driver:v0.0.7

and a look at /proc/bus/devices/usb finds my controller:

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=1bad ProdID=0002 Rev= 1.03
S:  Manufacturer=Harmonix Music
S:  Product=Harmonix Guitar for Xbox 360
S:  SerialNumber=004062D3
C:* #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=5d Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=4ms
E:  Ad=02(O) Atr=03(Int.) MxPS=  32 Ivl=8ms
I:  If#= 1 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=5d Prot=03 Driver=(none)
E:  Ad=83(I) Atr=03(Int.) MxPS=  32 Ivl=2ms
E:  Ad=04(O) Atr=03(Int.) MxPS=  32 Ivl=4ms
E:  Ad=85(I) Atr=03(Int.) MxPS=  32 Ivl=64ms
E:  Ad=05(O) Atr=03(Int.) MxPS=  32 Ivl=16ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=5d Prot=02 Driver=(none)
E:  Ad=86(I) Atr=03(Int.) MxPS=  32 Ivl=16ms
I:  If#= 3 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=fd Prot=13 Driver=(none)

But when I fire up FretsOnFire, it can't find the controller.  Routines like 'jscal' can't find the joystick.  So I'm not sure where to go next.

Help?  Thanks?
Sandy


How do I get from this point to having it actually work in FretsonFire?

---

