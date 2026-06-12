---
title: "install and use phone/modem Huawei ets 2258"
date: 2009-04-08
forum: General Help
---

### Post by bmatloob on 2009-04-08
Hi everybody, 

I am new to ubuntu and to Linux. I installed Ubuntu 8.10 recently. When using Windows XP I used to connect to the internet through phone/modem Huawei ets 2258 with no troubles. 
However, it is not working with ubuntu, and I don't have the installation package under Linux for that modem. 

Anyone can help please?

---

### Post by GeorgeVita on 2009-04-08
Hi **bmatloob**,

boot without Huawei ETS2258, wait for the system to stabilize, connect the modem, wait some seconds, open a terminal window (Applications, Accessories, Terminal) and run the command: **dmesg**
Scroll down to see messages like:
... TI USB 3410 1 port adapter converter now attached to ttyUSB0
or ... usb 1-1: configuration #1 chosen from 1 choice

Copy paste here these lines.

From terminal window (modem attached) run:
**lsusb**
**ls /dev/ttyU* /dev/ttyS* /dev/ttyA***

Copy here all responses.

Regards,
George



Tip: from Applications, Accessories, **right click** Terminal to **Add this launcer to panel**. Do the same for **Text Editor** and System, Administration, **System Monitor**. It will be more convenient for debugging and later to know the 3G data traffic (from system monitor).

---

### Post by bmatloob on 2009-04-09
Hi George, 
Thanks for your reply, and below are the responses to the commands you gave. 

Thanks and waiting to hear your advise. 

Bassam

dmesg 
[  297.882066] usbserial: USB Serial support registered for generic
[  297.882678] usbcore: registered new interface driver usbserial_generic
[  297.882696] usbserial: USB Serial Driver core
[  297.901071] usbserial: USB Serial support registered for TI USB 3410 1 port adapter
[  297.903800] usbserial: USB Serial support registered for TI USB 5052 2 port adapter
[  297.906607] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[  297.906632] firmware: requesting ti_usb-3410.bin
[  297.922129] usb 4-1: ti_download_firmware - firmware not found
[  297.924327] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
[  297.926931] usbcore: registered new interface driver ti_usb_3410_5052
[  297.926949] ti_usb_3410_5052: TI USB 3410/5052 Serial Driver v0.9

lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ls /dev/ttyU* /dev/ttyS* /dev/ttyA*
ls: cannot access /dev/ttyU*: No such file or directory
ls: cannot access /dev/ttyA*: No such file or directory
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3

---

### Post by GeorgeVita on 2009-04-09
> **bmatloob said:**
> ...
[  297.906632] firmware: requesting ti_usb-3410.bin
[  297.922129] usb 4-1: ti_download_firmware - firmware not found
[  297.924327] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
...


The above error can be possibly solved following post#2 of:
[http://ubuntuforums.org/showthread.php?p=6183236](http://ubuntuforums.org/showthread.php?p=6183236)

Try it, repeat the previous (dmesg, lsusb, ls /dev/ttyU*) and post new output.

G

---

### Post by bmatloob on 2009-04-10
Here is what I did and what I got ...

sudo cp /lib/firmware/$(uname -r)/ti_3410.fw /lib/firmware/ti_usb-3410.bin

dmesg
[  448.500094] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  448.755245] usb 4-1: configuration #1 chosen from 1 choice
[  448.759266] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[  448.759291] firmware: requesting ti_usb-3410.bin
[  449.364132] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[  449.507193] usb 4-1: device firmware changed
[  449.508842] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5
[  449.515984] usb 4-1: USB disconnect, address 4
[  449.684124] usb 4-1: new full speed USB device using uhci_hcd and address 5
[  449.907518] usb 4-1: configuration #1 chosen from 2 choices
[  449.913316] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[  449.913929] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5

lsusb: 
Bus 004 Device 005: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller

ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory

ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3

ls /dev/ttyA*
ls: cannot access /dev/ttyA*: No such file or directory

---

### Post by GeorgeVita on 2009-04-10
... found at: [https://answers.launchpad.net/ubuntu/+question/51120](https://answers.launchpad.net/ubuntu/+question/51120)

as I understand you must create a new rule file:
from terminal window: **sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules**

Copy paste the following:

[B]SUBSYSTEM=="usb_device" ACTION=="add"
SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \
SYSFS{bNumConfigurations}=="2" \
SYSFS{bConfigurationValue}=="1" \
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"[/B]

Save, exit from gedit, reboot without modem, attach it ... and good luck!

Note: As I don't have a "direct" experience with your modem, I am just searching in parallel with you to find the solution.

Regards,
George

---

### Post by bmatloob on 2009-04-10
did as advised, and get the following: 

[  516.744177] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  516.943718] usb 4-1: configuration #1 chosen from 1 choice
[  516.948177] ti_usb_3410_5052 4-1:1.0: TI USB 3410 1 port adapter converter detected
[  516.948203] firmware: requesting ti_usb-3410.bin

and dmesg keep saying requesting ti_usb-3410.bin for about 3 minutes and then dmesg adds extra messages as: 

[  576.960477] usb 4-1: ti_download_firmware - firmware not found
[  576.961089] ti_usb_3410_5052: probe of 4-1:1.0 failed with error -5

Thanks for all your help. If you figure out something new later, please post it.

---

### Post by GeorgeVita on 2009-04-10
Hi again,

tired searching but found:
[http://www.ubuntu.or.tz/index.php/technical-assistance/howtos/3-huawei-fixed-wireless-terminal-ets2288-modem-with-ubuntu-804](http://www.ubuntu.or.tz/index.php/technical-assistance/howtos/3-huawei-fixed-wireless-terminal-ets2288-modem-with-ubuntu-804)

related to ETS2288 modem, this document says the same you did adding **detach & attach the modem**looking at the output of **dmesg -c** to find the ttyUSB0 note!

> Therefore we run the command dmesg -c after plugging in the Modem to see what the system tells us. Most likely we will see a message that the modem is not recognized, which looks like this:


ti_usb_3410_5052 1-1:1.0: TI USB 3410 1 port adapter converter detected

ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

But don't worry, we can change this. We just have to add a new udev-rules file in our udev folder by typing the following:
sudo touch /etc/udev/rules.d/026_ti_usb_3410.rules

Now we can edit this file with our favourite text editor and add this content to it:
#TI USB 3410
SUBSYSTEM==&#8221;usb_device&#8221; ACTION==&#8221;add&#8221; SYSFS{idVendor}==&#8221;0451&#8243;,SYSFS{idProduct}==&#8221;3410&#8243; \
SYSFS{bNumConfigurations}==&#8221;2&#8243; \
SYSFS{bConfigurationValue}==&#8221;1&#8243; \
RUN+=&#8221;/bin/sh -c &#8216;echo 2 > /sys%p/device/bConfigurationValue''


If we plug the modem on and off again we should receive something like the following by typing dmesg -c:

[ 150.752279] hub 3-0:1.0: unable to enumerate USB device on port 4
[ 150.992278] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 151.185668] usb 2-2: configuration #1 chosen from 1 choice
[ 151.375847] usbcore: registered new interface driver usbserial
[ 151.376581] /build/buildd/linux-ports-2.6.25/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 151.377622] usbcore: registered new interface driver usbserial_generic
[ 151.377627] /build/buildd/linux-ports-2.6.25/drivers/usb/seria/etc/udev/rules.d/026_ti_usb_3410.rulesl/usb-serial.c: USB Serial Driver core
[ 151.382826] /build/buildd/linux-ports-2.6.25/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
[ 151.384064] /build/buildd/linux-ports-2.6.25/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
[ 151.385227] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
[ 152.024345] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[ 152.166531] usb 2-2: device firmware changed
[ 152.166567] usb 2-2: USB disconnect, address 2
[ 152.166792] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[ 152.280361] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 152.500805] usb 2-2: configuration #1 chosen from 2 choices
[ 152.504762] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
[ 152.504784] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[ 152.504816] usbcore: registered new interface driver ti_usb_3410_5052
[ 152.504824] /build/buildd/linux-ports-2.6.25/drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9
[ 152.604585] ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected
[ 152.607216] usb 2-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0

If so we should now have a new entry called /dev/ttyUSB0


Also searching for **"ti_usb_3410_5052" ubuntu solved** returns 115 hits!

**You can check:**
a. the contents of the rules file: **cat /etc/udev/rules.d/026_ti_usb_3410.rules**
b. if firmware file exists: **ls /lib/firmware/ti_usb-3410.bin**

Do not update the kernel as you have 8.10 and the above link talks about 8.04
If you want to edit the rule file use **sudo gedit ...** instead of sudo touch ...

---

### Post by bmatloob on 2009-04-23
Hi George, 

Sorry for the late reply, I was busy with Easter days and work. 
But anyway, I am happy to tell you that finally the USB modem was identified through following your guidance. 

One note though, for some reason, if the USB modem got an address of 3 or more, it will not work and will not attached to ttyUSB0. 

What I am doing, is unplugging all my USB devices, and have the modem only be connected on the boot. Doing this will assign the USB port the address 2 and ultimately will attached to ttyUSB0

Thanks much again. 

Bassam

---

### Post by trollboy on 2009-06-17
I've got a different modem, but same goofy chipset.  I'm running F10, and its not mapping to /dev/usbtty0, anyone got any thoughts with this:
DMESG:
ti_usb_3410_5052: version magic '2.6.9-42.EL 686 REGPARM 4KSTACKS gcc-3.4' should be '2.6.29.4-167.fc11.i686.PAE SMP mod_unload 686 '
usb 3-1: new full speed USB device using uhci_hcd and address 3
usb 3-1: New USB device found, idVendor=06e0, idProduct=f111
usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 3-1: Product: TUSB3410 Serial Port
usb 3-1: Manufacturer: Texas Instruments
usb 3-1: configuration #1 chosen from 1 choice

LSUSB:
[root@smsserver1 ~]# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 06e0:f111 Multi-Tech Systems, Inc. 
Bus 003 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


(The Prolific Technology is a Serial to USB adaptor connected to another modem that comes with a serial port.  It works fine, the problem I'm having is the other modem doesn't come up on /dev/ttyUSB1.  The other modem is showing up fine on /dev/ttyUSB0.) Any help would be appreciated.

---

### Post by GeorgeVita on 2009-06-17
Hi **trollboy**,
have you tried to use usbserial driver?

**sudo modprobe usbserial vendor=0x06e0 product=0xf111**

It will possibly create /dev/tty**XYZn** (it is not always /dev/ttyUSBn).

You should check ls /dev/tty* before and after attaching the peripheral (also dmesg will report it).

Good luck!
George

---

### Post by virginbala on 2009-07-28
it's ur port /dev/ttyUSB0? which version kernel do u have? i've also huawei ets 2288 same like u.. it's working fine.. tel me clearly i'll resolve......

thx

---

### Post by ksolomon on 2009-07-28
Hi, I use HUAWEI modem too and I got a different problem. After I read your problem<also everyone who got the same problem> and your solving, I can config my ubuntu to connect to internet.But, just today when I try to connect again it told:

ksolomon@ksolomon-laptop:~$ dmesg
[   64.925017] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   65.124812] usb 2-2: configuration #1 chosen from 1 choice
[   65.180847] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   65.195877] usbcore: registered new interface driver ndiswrapper
[  388.288096] usb 2-2: USB disconnect, address 2

instead.

and then you know.. no such file or directory for ttyUSB0.

= =''

I don't know how to deal with that and I've searched for many websites but nothing.I'm a ubuntu newbie but I really love it. ^^''

thank you!!

---

### Post by virginbala on 2009-07-28
don't worry about [COLOR=Magenta]dmesg[/COLOR] it's always shown error.. did u created rules file? make sure don't create [COLOR=Magenta]rules file[/COLOR] cos not working anymore, do u have wvdial files ? no mean ask [COLOR=Lime]georgevita[/COLOR] he'll give u 5 files [COLOR=Red].DEB[/COLOR] just install and do make dialler file u'll connect internet,

---

### Post by virginbala on 2009-07-28
here is the 5 files link download and install

[http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
[http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
[http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
[http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
[http]("http://packages.ubuntu.com/jaunty/i386/wvdial/download")[://packages.ubuntu.com/jaunty/i386/wvdial/download]("http://packages.ubuntu.com/jaunty/i386/wvdial/download")

aftr that go to terminal type:
sudo -i  (password)
gedit /etc/wvdial.conf

[COLOR=Cyan]**copy and paste  this line**[/COLOR]

[COLOR=Red][Dialer huawei]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = “username”
Password = “password”
PPPD Options = crtcts multilink usepeerdns lock defaultroute[/COLOR]

---

### Post by ksolomon on 2009-07-29
Yep, I've already done all you told me. And, I used to use my internet through wvdial for long time, but just then I've got that message and I can't connect to internet anymore according to it can't find "ttyUSB0" and I've checked all configuration but it still the same.So, I guest that I've done something that changed the configuration about USB driver.If you've anyway to rollback USB driver might be ok I think.

---

### Post by ksolomon on 2009-08-01
> **virginbala said:**
> don't worry about [COLOR=Magenta]dmesg[/COLOR] it's always shown error.. did u created rules file? _***make sure don't create [COLOR=Magenta]rules file[/COLOR] cos not working anymore***_, do u have wvdial files ? no mean ask [COLOR=Lime]georgevita[/COLOR] he'll give u 5 files [COLOR=Red].DEB[/COLOR] just install and do make dialler file u'll connect internet,


Thanks to Virginbala. I've forgotten to delete rules file, but now I've deleted it.So, it can connect now. THX.

---

### Post by ramnarayan on 2009-09-10
> **virginbala said:**
> it's ur port /dev/ttyUSB0? which version kernel do u have? i've also huawei ets 2288 same like u.. it's working fine.. tel me clearly i'll resolve......

thx

Hi

I have 9.04, huawei ets 2288 and kernel 2.6.28.15 and this device does not work.

So how exactly did yo get it to work, will be *extremely grateful*

ram

---

### Post by nidhi1500 on 2009-10-12
my modem is ets 1201. i type in root  
ls /dev/ttyS*
this result show
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
so how to creat  
gedit /etc/udev/rules.d/026_ti_usb_3410.rules
this file

---

### Post by ramnarayan on 2009-10-17
Hi Nidhi,

at pasting below your quote the way to make the rules file and the contents - which are for my ets 2288 model, am not sure if its the same for yours ( i think it should be)

> **nidhi1500 said:**
> my modem is ets 1201. i type in root  
ls /dev/ttyS*
this result show
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
so how to creat  
gedit /etc/udev/rules.d/026_ti_usb_3410.rules
this file

**
at the command line after you do:
gedit /etc/udev/rules.d/026_ti_usb_3410.rules

paste the following lines exactly

```
#TI USB 3410

SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \

SYSFS{bNumConfigurations}=="2" \

SYSFS{bConfigurationValue}=="2" \

RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"
```

save and exit

unplug your usb device 
replug after a about 15 seconds and run
$dmesg

this should show a message saying that your device is not attached to ttyUSB0

regards
ram

---

### Post by ramnarayan on 2009-10-17
> **ramnarayan said:**
> Hi

I have 9.04, huawei ets 2288 and kernel 2.6.28.15 and this device does not work.

So how exactly did yo get it to work, will be *extremely grateful*

ram

Just to say that to get this device to work on 8.04.1 and 8.10 needs an additional step

for complete information sake am putting the steps down here again (with the new step marked)

Step 1. create a file
sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules
paste the following into it 
```

#TI USB 3410

SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \

SYSFS{bNumConfigurations}=="2" \

SYSFS{bConfigurationValue}=="2" \

RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'" 
```

save and exit

Step 2: THE NEW STEP

```
sudo cp /lib/firmware/$(uname -r)/ti_3410.fw /lib/firmware/ti_usb-3410.bin
```

this will place the firmware where it should be 

Step 3 - create/ edit a wvdial.conf file

```
sudo gedit /etc/wvdial.conf
```

and paste the following contents

```
[Dialer FOO_any_name_you_want]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777 
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = your phone number
Password = your pass word (which is usually your phone number)
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap nobsdcomp nodeflate
```

Step 4 Unplug your device, replug after about 10 - 15 seconds
 run
$ dmesg

your device should show up as attached to /dev/ttyUSB0

run
$ wvdial fooname

and it should work

***
i reverted to 8.10 because this device stubbornly refuses to work on 9.04 - hope 9.10 Karmic Koala serves better

ram

---

### Post by majikins on 2009-10-19
Hi

I still have not got this right on jaunty - I have downloaded and installed the debs as suggested - ttyUSB0 and 1 was setup on install but upon reboot was not then mapped.

Any further suggestions?

M

---

### Post by ramnarayan on 2009-10-19
> **majikins said:**
> Hi

I still have not got this right on jaunty - I have downloaded and installed the debs as suggested - ttyUSB0 and 1 was setup on install but upon reboot was not then mapped.

Any further suggestions?

M

as mentioned earlier - this device *does not* work on 9.04 (jaunty) there is some stupid bug that is as yet unresolved. Thats why i have reverted to 8.10

ram

---

### Post by majikins on 2009-10-26
Hi

Loaded 8.10 and it still does not work!!

I've just realised something - in this part of the world, South Africa it seems the ets 2258 is a different device to what is talked about here.

lsusb gives:
Bus 005 Device 002: ID 12d1:1010 Huawei Technologies Co., Ltd.

which has a different ID to the solution above.

dmesg gives:
 352.608019] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  352.850125] usb 5-1: configuration #1 chosen from 1 choice
[  352.940690] usbcore: registered new interface driver libusual
[  352.958224] Initializing USB Mass Storage driver...
[  352.960087] scsi4 : SCSI emulation for USB Mass Storage devices
[  352.961390] usbcore: registered new interface driver usb-storage
[  352.961397] USB Mass Storage support registered.
[  352.962912] usb-storage: device found at 2
[  352.962918] usb-storage: waiting for device to settle before scanning
[  357.961309] usb-storage: device scan complete
[  357.973297] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  358.021395] sr1: scsi-1 drive
[  358.021753] sr 4:0:0:0: Attached scsi CD-ROM sr1
[  358.022086] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  367.288040] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  367.555484] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  367.555500] sr: Sense Key : No Sense [current] 
[  367.555504] sr: Add. Sense: No additional sense information
[  368.783318] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  368.783333] sr: Sense Key : No Sense [current] 
[  368.783337] sr: Add. Sense: No additional sense information
[  372.293098] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  372.293119] sr: Sense Key : No Sense [current] 
[  372.293124] sr: Add. Sense: No additional sense information
[  372.305098] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
[  372.305116] sr: Sense Key : No Sense [current] 
[  372.305121] sr: Add. Sense: No additional sense information
[  372.317092] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
[  372.317111] sr: Sense Key : No Sense [current] 
[  372.317116] sr: Add. Sense: No additional sense information
[  372.353070] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  372.353090] sr: Sense Key : No Sense [current] 
[  372.353095] sr: Add. Sense: No additional sense information
[  372.389052] ISO 9660 Extensions: Microsoft Joliet Level 3
[  372.421059] ISOFS: changing to secondary root

its obviously being recognised as a storage device first.

can anyone help with this?

M

---

### Post by surendra suwal on 2009-11-20
> **virginbala said:**
> here is the 5 files link download and install

[http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
[http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
[http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
[http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
[http]("http://packages.ubuntu.com/jaunty/i386/wvdial/download")[://packages.ubuntu.com/jaunty/i386/wvdial/download]("http://packages.ubuntu.com/jaunty/i386/wvdial/download")

aftr that go to terminal type:
sudo -i  (password)
gedit /etc/wvdial.conf

[COLOR=Cyan]**copy and paste  this line**[/COLOR]

[COLOR=Red][Dialer huawei]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = “username”
Password = “password”
PPPD Options = crtcts multilink usepeerdns lock defaultroute[/COLOR]




hi fren i am also using ubuntu 9.10
ans using same  classic Huawei ets 2258 male usb to male usb  but it not connected in internet

i am using fix wireless modem phone so please any one help me to connect to internet
and i also try to all of these but not work

---

### Post by rajeshram312 on 2010-05-04
Dear sir,
plz mail my id 2258 setup **_\HUAWEI\MODEM_**, **_setup_**

---

### Post by rajeshram312 on 2010-05-04
plz sir mail me

---

