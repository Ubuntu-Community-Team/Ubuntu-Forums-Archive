---
title: "USB device not mounting"
date: 2006-06-23
forum: Desktop Environments
---

### Post by madanasta on 2006-06-23
Hello all

This is my first post in these forums as I installed Ubuntu a few days ago. The installation was a great success but that's a topic for another thread, I guess. On to my question.

I have a basic knowledge of Linux but, evidently, not enough to know what's going on. The problem is that, while trying to follow a HowTo on synce to setup syncing between my Dapper system and my Qtek 9100 (WM2005), I can't get the pda mounting (please correct my terminology if I am wrong). When I connect the pda to the pc through usb, the device is shown on the Device Manager and found by other utils (see below), but no entry (/dev/ttyUSB? or anything else) appears for it.

Some outputs while trying to fix, please tell me if something more is needed:

lsusb:
```
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
**Bus 002 Device 006: ID 0bb4:0bce High Tech Computer Corp**.
Bus 002 Device 001: ID 0000:0000
```
(related line in bold, the pda is indeed manufactured by HTC).

lshw -businfo | grep usb:
```
usb@1        usb1       bus            UHCI Host Controller
usb@1:1                 input          Microsoft 3-Button Mouse with IntelliEye(TM)
usb@2        usb2       bus            UHCI Host Controller
**usb@2:2                 generic        Generic RNDIS**
usb@3        usb3       bus            UHCI Host Controller
usb@4        usb4       bus            EHCI Host Controller
```

lshw -C generic:
```
*-usb UNCLAIMED
       description: Generic USB device
       product: Generic RNDIS
       vendor: HTC
       physical id: 2
       bus info: usb@2:2
       version: 0.00
       capabilities: usb-2.00
       configuration: maxpower=100mA speed=12.0MB/s
```

dmesg (last two lines, when device is disconnected and immediately reconnected):
```
[17182039.888000] usb 2-2: USB disconnect, address 6
[17182043.656000] usb 2-2: new full speed USB device using uhci_hcd and address 7
```

From what I can understand, the pda is indeed recognized as a piece of hw connected on a usb port, but it is not mounted. Is this correct? Is it a matter of a module required for the device to mount not being present?

Again, pls forgive my noob terminology or the fact that I may've posted in the wrong forum, I posted here because this seems like a general hw mounting question.

Thanx to all

mada

---

### Post by ifokkema on 2006-06-23
Hi,

I'm going to try and give some suggestions, although I would like to warn you beforehand: don't have experience with your specific problem.

[QUOTE=madanasta]I have a basic knowledge of Linux (...)[/QUOTE]
Well, I've been using Linux for quite a few years now, and I've just seen you spit out commands that I didn't know of :)

[QUOTE=madanasta]From what I can understand, the pda is indeed recognized as a piece of hw connected on a usb port, but it is not mounted. Is this correct? Is it a matter of a module required for the device to mount not being present?

Again, pls forgive my noob terminology or the fact that I may've posted in the wrong forum, I posted here because this seems like a general hw mounting question.[/QUOTE]
You are very right to conclude your system recognized the device properly and it doesn't get mounted. If your dmesd doesn't show anything more than what you've sent us, no process starts the device scan and mount process etc.

Try, while having the device connected:
```
sudo /etc/init.d/hotplug restart
```

---

### Post by madanasta on 2006-06-26
It might sound funny but there is no hotplug in /etc/init.d, so I cannot run the command you suggested. locate hotplug also did not reveal anything useful apart from a kernel module. I don't even have a /sbin/hotplug :confused: 

I feel I should start reading about hotplugging in Ubuntu ](*,) 

Also, thanks for your kind words. I have to admit that it's not been long since I came across these commands in forums, etc, though their use was clear enough.

Thanks for your help

mada

---

### Post by madanasta on 2006-06-26
I found this

> Yes, dapper droppt the hotplug package. All hotplugging is now handled
by udev. udev itself only handles device creation and things like that
and then calls HAL. HAL then collects informations about the new device
and decides what to do (e.g. using pmount to mount storage devices).

here:

[http://ubuntuforums.org/showthread.php?t=193082&page=3](http://ubuntuforums.org/showthread.php?t=193082&page=3)

More reading ahead :) 

mada

---

### Post by madanasta on 2006-06-26
It turns out that, for Dapper, the right form of the command ifokkema has suggested is

```
sudo /etc/init.d/udev restart
```

since Dapper uses udev rather than hotplug.

However, this changes nothing: dmesg still shows that the usb device is connected but not mounted. Also, the usbserial module is there (modprobe usbserial does not output anything) and I understand that this is the right driver (I might be wrong). Could this be a case where the kernel does not know that it should use this driver for this particular usb device? If yes, how can I tell it to?

mada

---

### Post by ifokkema on 2006-06-27
[QUOTE=madanasta]It turns out that, for Dapper, the right form of the command ifokkema has suggested is

```
sudo /etc/init.d/udev restart
```

since Dapper uses udev rather than hotplug.[/QUOTE]
Wow... thanks for letting me know. Linux distributions evolve and continue to get more advanced. It happens sometimes that I find out there's a GUI method of doing things nowadays, but this is good to know. Ah well, before hotplug there was discover, so we'll keep on switching... :)

[QUOTE=madanasta]However, this changes nothing: dmesg still shows that the usb device is connected but not mounted. Also, the usbserial module is there (modprobe usbserial does not output anything) and I understand that this is the right driver (I might be wrong). Could this be a case where the kernel does not know that it should use this driver for this particular usb device? If yes, how can I tell it to?[/QUOTE]
Well, let's continue with our new knowledge :)
- Did you check for the packages hal and udev to be installed properly? (I assume you do ;))
- When your device is connected, try
```
lsmod |grep usb
```
to see what USB drivers you have. Usbstorage should take on your drive. Please try
```
sudo modprobe usb_storage
```
Maybe after that:
```
sudo /etc/init.d/udev restart
```
;)

---

### Post by madanasta on 2006-06-28
> **ifokkema]- Did you check for the packages hal and udev to be installed properly? (I assume you do  said:**
> 

It didn't occur to me to verify that as connecting a usb stick worked as it should: A device was automatically created and a link popped-up on the desktop.

Both udev and hal show up in Synaptic as installed and up-to-date. I don't know of any other way to check their status (told ya my knowledge is basic ;) ), although I'd like to, preferably at command-line level.

[QUOTE=ifokkema]- When your device is connected, try
```
lsmod |grep usb
```
to see what USB drivers you have. Usbstorage should take on your drive.

Having read around a bit on connecting a pda, I believe that it is the usbserial module that should do that (which is installed).

Here's the output, not very engouraging :( :

```
usbhid             39904    0
usbcore           130692    4    usbhid,ehci_hcd, uhci_hcd
```

[QUOTE=ifokkema]Please try
```
sudo modprobe usb_storage
```[/QUOTE]

Did that, also for usbserial, so lsmod | grep usb now lists those packages, too. However, still no progress: The device is not mounted, even if I disconnect and reconnect it.

[QUOTE=ifokkema]Maybe after that:
```
sudo /etc/init.d/udev restart
```[/QUOTE]

That didn't help either.

I still suspect that the kernel sends a message to udev, but udev in turn does not know that it should use the usb_storage or usbserial modules to mount the device. I understand that there are rule files in /etc/udev/rules.d that specify how udev handles messages, I'm reading about all that now and will come back, hopefully with results :confused: 

Thanx for all your help so far :D 

mada

---

### Post by ifokkema on 2006-06-28
> **madanasta]It didn't occur to me to verify that as connecting a usb stick worked as it should: A device was automatically created and a link popped-up on the desktop.[/QUOTE]
OK - I didn't know you didn't have any problems with other USB devices. I don't know much about PDA's to Linux, but I think I got a little farther.

[QUOTE=madanasta]Both udev and hal show up in Synaptic as installed and up-to-date. I don't know of any other way to check their status (told ya my knowledge is basic  said:**
> 
The command to use is dpkg. Dpkg handles the packages in Ubuntu and there are lots of options (see 'man dpkg'). In this case you need:
```
dpkg -l hal udev
```
'ii' at the left means it's all OK.

[QUOTE=madanasta]Having read around a bit on connecting a pda, I believe that it is the usbserial module that should do that (which is installed).
OK, I did some reading, too. There are a few drivers in Linux that are in the 'USB/serial' section. One of them is ipaq, and from what I understood, that may work with your PDA, too.

[QUOTE=madanasta]I still suspect that the kernel sends a message to udev, but udev in turn does not know that it should use the usb_storage or usbserial modules to mount the device. I understand that there are rule files in /etc/udev/rules.d that specify how udev handles messages, I'm reading about all that now and will come back, hopefully with results :confused:[/QUOTE]
Wow, you're really teaching me, too :)
Nice list. It seems udev reads out the information and depending on that set of rules, decides which modules to load.
To check out all modules available for your kernel, see this directory:
```
/lib/modules/[your_kernel_version]/kernel/drivers
```
to see your current kernel version:
```
uname -r
```

Do you have the gnome-pilot package installed? Not sure what it does, but it may help. There's also p3nfs, but I'm not sure if that's also for USB connections.

Hope you're getting any further...

---

### Post by madanasta on 2006-06-28
Moved on a bit.

First, as to your suggestions... the ipaq-module-related one has pointed me towards the direction that finally provided some useful answers... thanks ;).

```
dpkg -l hal udev
```
does list the hal and udev packages.

Then

```
ls /lib/modules/`uname -r`/kernel/drivers/usb/serial
```
indeed kontains a number of drivers, including the usbserial.ko and ipaq.ko ones.

So, what I found is that vendor and product id parameters must not be specified to udev, but to the ipaq driver, instead (now this has really confused me :confused:, I feel I know absolutely nothing on how Linux handles hotplugging and module loading)!

What I did was follow the instructions at [http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php), although my post was not originally about making synce work, but about getting the pda to mount as a usb device. Based on the howto, I managed to retrieve vendor and product id information, which is the following:

```
> T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
> D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
> P:  **[COLOR="Red"]Vendor=0bb4 ProdID=0bce[/COLOR]** Rev= 0.00
> S:  Manufacturer=HTC
> S:  Product=Generic RNDIS
> C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=100mA
> I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
> E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
> I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
> E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
> E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```
Then, by manually loading usbserial and ipaq (as they weren't configured to load at boot time, otherwise I'd have to rmmod them and then manually load) specifying vendor and product id parameters to the latter, I managed to make a difference :p:

```
modprobe usbserial
modprobe ipaq [COLOR="Red"]**vendor=0x0bb4 product=0x0bce**[/COLOR]
```
Then, connecting the pda resulted in the following dmesg output:

```
[17179920.296000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[B][COLOR="Red"][17179920.440000] ipaq 2-2:1.0: PocketPC PDA converter detected
[17179920.440000] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
[17179920.440000] ipaq 2-2:1.1: PocketPC PDA converter detected
[17179920.440000] usb 2-2: PocketPC PDA converter now attached to ttyUSB1
[/COLOR][/B][17179920.688000] Unable to handle kernel NULL pointer dereference at virtual address 0000002c
...
(a magnificent load of error and debug messages follows)
...
```
The errors are clearly explained in the howto and the related bug report about using synce with WM5 devices at [https://sourceforge.net/tracker/index.php?func=detail&aid=1332550&group_id=30550&atid=399601](https://sourceforge.net/tracker/index.php?func=detail&aid=1332550&group_id=30550&atid=399601). But, remember, this post was not about synce, but about making a driver take over and mount the device. As the dmesg dump clearly shows, this has been achieved, no matter if it fails later on for synce-specific reasons.

So, bottomline is that I got really confused as to how the ipaq module was selected (by udev, I suppose?) to handle a newly connected usb device, just by specifying vendor and product id info *to the module* itself. Next step for me is read about such stuff that sounds like pretty essential Linux architecture stuff... not understanding them makes me feel pretty embarassed and helpless.

Ifokkema, thank you for your useful, eager and good-hearted help =D>, I hope we'll be talking again in these forums soon!

I also hope that synce solves all these WM5-related problems so that I'll be able to sync my pda with my Dapper laptop ;)

Cheers

mada

---

### Post by edmondt on 2007-01-22
I have a Dopod 818 Pro and I'm on ubuntu 6.10 when I run this command:

edmondt@edmond-laptop:~$ lshw -businfo | grep usb
WARNING: you should run this program as super-user.
usb@1        usb1      bus            UHCI Host Controller
**usb@1:1                generic        Generic RNDIS**
usb@2        usb2      bus            UHCI Host Controller
usb@2:2                bus            Logitech BT Mini-Receiver
usb@2:2.2              input          Logitech BT Mini-Receiver
usb@2:2.3              input          Logitech BT Mini-Receiver
usb@3        usb3      bus            UHCI Host Controller
usb@4        usb4      bus            EHCI Host Controller
usb@4:3                storage        USB TO IDE
usb@4:6                bus            USB2.0 Hub Controller
usb@4:6.1              printer        PSC 750
usb@4:6.4              bus            USB2.0 Hub Controller

I couldn't see ttyUSB0 for my Generic RNDIS (Dopod 818 Pro)

There is this usb-rndis-lite driver from here:

[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)

maybe it can help somehow...

---

### Post by edmondt on 2007-01-23
I also found this link:

[http://www.mail-archive.com/synce-devel@lists.sourceforge.net/msg00212.html](http://www.mail-archive.com/synce-devel@lists.sourceforge.net/msg00212.html)

---

### Post by eudemus on 2007-04-23
Madanasta,
Was it these commands
modprobe usbserial
modprobe ipaq vendor=0x0bb4 product=0x0bce
that made the difference in your case?

It sounds very very similar to what I'm trying to do - I want to have the PDA mounted properly so that I can use syncing software to synchronise all the data on the SD card of the PDA with a hard drive directory.

Can you go through again for a non-technical user how you got the PDA to be not just detected but properly mounted, please?
Thanks

Eudemus

---

### Post by madanasta on 2007-04-24
Eudemus and all

Since my last post on this thread, I have temporarily abandoned any attempts to connect my WM5 PDA and hopefully sync it, mainly because I was waiting for better support for WM5. So, it's been some time since I last looked-into the issue but yes, as far as I can remember, these two commands are the ones that enabled me to have my PDA mounted as a USB device upon connection (to be more specific, have the ipaq module handle the PDA when udev sends a message about it having been connected). I got no further than that, but will possibly look into the issue further now, thanks to the occasion :).

As for step-by-step description of what I did, I am afraid I cannot provide that now as I have really forgotten the exact steps I followed back then (in fact, I am out of a Linux installation right now so I can't even try it again :(). I do remember, though, that I followed SynCE's HowTo ([http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php)) which has a lot of details and instructions on detecting the PDA and finding out various bits of information about it (class, vendor, etc.), apart from using it with SynCE. I hope this helps for now.

madanasta

---

### Post by eudemus on 2007-04-24
Madanasta,
I've tried the two commands that you mentioned above. No difference.
Looking back through your comments on the thread, you suggest that if in response to dmesg I get:

[17180469.772000] usb 2-1: new full speed USB device using ohci_hcd and address 5
[17180469.984000] ipaq 2-1:1.0: PocketPC PDA converter detected
[17180469.988000] usb 2-1: PocketPC PDA converter now attached to ttyUSB0

this means that my PDA is mounted, just some synce thing getting in the way, somehow ....
I don't really understand what you mean by that, or how to resolve it.
anyhow, I'm not really any further on.
I can't use Unison to sync, and even OpenOffice behaves weirdly when saving to folders on the PDA (though they do appear in the directory tree when saving from OpenOffice.)

All help much needed & much appreciated.
Eudemus

---

### Post by ifokkema on 2007-04-25
> **eudemus said:**
> 
[17180469.772000] usb 2-1: new full speed USB device using ohci_hcd and address 5
[17180469.984000] ipaq 2-1:1.0: PocketPC PDA converter detected
[17180469.988000] usb 2-1: PocketPC PDA converter now attached to ttyUSB0

this means that my PDA is mounted, just some synce thing getting in the way, somehow ....
Actually, this message does not mean it gets mounted. It only means there is now a connection. Mounting may take place automatically, but this is very dependent on your settings and such, and I don't assume this is the case.

But anyhow, if the message says it's connected to ttyUSB0, you'll need to use /dev/ttyUSB0 to talk to the device.

Can you get any further from here? Try
```
sudo fdisk -l /dev/ttyUSB0
```
to check out the found partitions, which you can mount manually (see `man mount` if you're unsure how to).

---

### Post by alisaza on 2007-04-25
Try this and post results
sudo tail -f /var/log/messages

---

