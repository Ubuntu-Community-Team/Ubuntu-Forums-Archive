---
title: "Dell and wireless broadband 5720"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by hggdh on 2007-11-09
I just got a 5720 wireless broadband from Dell. Good and nice.

This is a Novatel Wireless (rebranded by Dell) PCI-express card, that is installed in the laptop.

The problem... I cannot find any reference to what would be the original Novatel product. And... without it, it is getting sort of difficult to get it to work. Add to it the fact that my laptop is native Ubuntu; the only Windows I have is a VMWare XP guest.

And... I went on to activate the card -- which means installing the Dell-provided pile of trash in the XP guest, and miserabily failed: the installation starts, and immediately fails with a "Not a Dell compatible system".

Sigh. Called Dell support, and went thru the usual bump-up: first tech on the line did not even know what VMWare was; second and third same, fourth actually tried to help (but also had no idea on what I was talking about), finally got to a supervisor -- which bumped it to next level of support.

Dell position so far: "this is not a Dell installed OS, so we cannot help you".

My position so far: "this is a 100% original Dell system, with Dell parts. Your product fails to install". Of course, I am absolutely certain that the customer is *not* right here, so I decided to try here.

So. Again, this is the Wireless Broadband embedded card, 5720, USBid=413c:8133. I know it is Novatel Wireless because 'lsusb -v' reports this (output trimmed):

us 006 Device 002: ID 413c:8133 Dell Computer Corp. 
  (...)
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8133 
  bcdDevice            0.00
  iManufacturer           1 Novatel Wireless Inc.
  iProduct                2 Novatel Wireless CDMA

Anyone knows what model of Novatel this is, and how to get it activated?

---

### Post by hggdh on 2007-11-12
Some developments... some good, some bad. The Dell 5720 is indeed a Novatel Wireless. Novatel states the Verizon-compatible card (as used by Dell) is the ev620, with id 1410:2100, and it is indeed an USB modem.

Initially I though tI would be able to bring it up in Gutsy by forcing-load the usbserial module:

sudo modprobe usbserial vendor=413c product=8133

But this did not create any ttys, so... probably not compatible.

Then, looking at the USB serial modules, I found option.c. In option.c we *do* have the Novatel 1410:2100 defined as a supported device, so... it begged me to  hack in and add a new product -- one single line in... so I did it, and rebuilt the module, and rebooted.

Result: the modem is recognised:

[   32.570454] usbcore: registered new interface driver usbserial
[   32.570478] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   32.570533] usbcore: registered new interface driver usbserial_generic
[   32.570537] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   32.587753] drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   32.587808] option 5-2:1.0: GSM modem (1-port) converter detected
[   32.588062] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[   32.588076] option 5-2:1.1: GSM modem (1-port) converter detected
[   32.588202] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[   32.588217] usbcore: registered new interface driver option
[   32.588221] drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1

Now, all that is left is try to activate the bloody card to Verizon... this is a battle I will fight tomorrow.

Of course, I still have to verify the AT initialisation strings, but a quick first try shows the modem (at least) responded to basic commands:

Nov 11 22:43:33 localhost kernel: [  170.944041] PPP generic driver version 2.4.2
Nov 11 22:43:33 localhost pppd[7346]: pppd 2.4.4 started by root, uid 0
Nov 11 22:43:34 localhost chat[7348]: abort on (BUSY)
Nov 11 22:43:34 localhost chat[7348]: abort on (NO CARRIER)
Nov 11 22:43:34 localhost chat[7348]: abort on (NO ANSWER)
Nov 11 22:43:34 localhost chat[7348]: send (ATZ^M)
Nov 11 22:43:34 localhost chat[7348]: expect (OK)
Nov 11 22:43:34 localhost chat[7348]: ATZ^M^M
Nov 11 22:43:34 localhost chat[7348]: OK
Nov 11 22:43:34 localhost chat[7348]:  -- got it 
Nov 11 22:43:34 localhost chat[7348]: send (AT&F&D2&C1E0V1S0=0^M)
Nov 11 22:43:34 localhost chat[7348]: expect (OK)
Nov 11 22:43:34 localhost chat[7348]: ^M
Nov 11 22:43:34 localhost chat[7348]: AT&F&D2&C1E0V1S0=0^M^M
Nov 11 22:43:34 localhost chat[7348]: OK
Nov 11 22:43:34 localhost chat[7348]:  -- got it 
Nov 11 22:43:34 localhost chat[7348]: send (AT+IFC=2,2^M)
Nov 11 22:43:34 localhost chat[7348]: expect (OK)
Nov 11 22:43:34 localhost chat[7348]: ^M
Nov 11 22:43:34 localhost chat[7348]: ^M
Nov 11 22:43:34 localhost chat[7348]: OK
Nov 11 22:43:34 localhost chat[7348]:  -- got it 
Nov 11 22:43:34 localhost chat[7348]: send (ATD#777^M)
Nov 11 22:43:34 localhost chat[7348]: expect (CONNECT)
Nov 11 22:43:34 localhost chat[7348]: ^M
Nov 11 22:43:35 localhost chat[7348]: ^M
Nov 11 22:43:35 localhost chat[7348]: NO CARRIER
Nov 11 22:43:35 localhost chat[7348]:  -- failed
Nov 11 22:43:35 localhost chat[7348]: Failed (NO CARRIER)
Nov 11 22:43:35 localhost pppd[7346]: Connect script failed

---

### Post by hggdh on 2007-11-29
No, no luck. No matter what, I always get the "No carrier" response.

I wonder if the basic initialisation of the device writes something to it -- sort of an activation command.

So I called Dell, and still did not get anywhere. The most I got them to do was to send me the Windows Vista CD (that, for whatever reason, I had not received -- not that I had worried about it before). I then set up another VMWare guest, now for Vista, and installed the CD. I then tried to install the bloody Dell package.

And again failed with a "not a Dell compatible system".

Ah well. I went on and expanded the Dell MSI package, and did find a DLL that issues this message. I could have gone ahead and hacked it off, but this would cost me time that I really do not have. I am guessing that it checks pieces of the BIOS for Dell-provided values. But I did take out the Windows drivers from the package (it will not install on Windows without the drivers provided by Dell, since the USB Id is Dell!), and installed them on the Vista and the XP images. Still I would be hit by a "no carrier" error when dialing out on the modem.

So, I took the last Dell support option: returned the card.

**Lessons:**

**1**. Dell seems to be requiring that a Dell device be installed on a Windows provided by Dell running on a Dell system. Be **extremely** carefull when buying Dell add-ons.

**2**. Newer Dell laptops seem to have dropped PCMCIA support. At least my Dell 1721 does not have it (and instead only one PCI-Express slot. This means that your old PCMCIA cards are unusable.

**3**. Dell does not clearly state (2) above. Had I known about it, I would certainly have thought very carefully on the this, and also certainly got another system, Dell or otherwise. Right now all my old PCMCIA cards are good only for paper weight. This specific card is cheap (sort of -- $150, thereabout), but when you have multiple PCMCIA cards, the cost adds up rather steeply.

**4**. Also related to (1) above -- be carefull if you buy a Dell add-on to run on a non-Dell system.

**5**. Also related to (1) and (4) above: if you do buy it, it might not install... Dell decided that Dell add-ons should only be used on Dell systems, it seems.

**6**. Final lesson: Dell still does not really get it. This was a pure Dell system, using nothing but Dell parts. But Linux support would not even hear me (I am running on a non-supported Linux laptop), and Windows support cannot understand that the problem is with the Dell MSI package they provide with the card, and the mind-bogglingly stupid test Dell implemented.

And... this is it, for me. For many years I have been a happy Dell customer. Right now I have, around me, 5 Dell systems -- all running Linux, either Ubuntu or Debian. But this is it.[COLOR="Red"] I am not going to buy Dell anymore[/COLOR].

For the record, I did contact Novatel support, asking for the Modem AT command set. Since it is highly possible I would need a particular sequence of modem commands to correctly set it up (and perhaps, activate it), then having the command set with the Novatel-specific implementation would really help. Unfortunately, my request to Novatel was never answered.

---

