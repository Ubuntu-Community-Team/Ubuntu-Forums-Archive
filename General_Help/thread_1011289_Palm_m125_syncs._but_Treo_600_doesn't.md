---
title: "Palm m125 syncs. but Treo 600 doesn't"
date: 2008-12-14
forum: General Help
---

### Post by ortenauer on 2008-12-14
Hello,

I'm stuck...after installing Ubuntu 8.10 everything worked fine, until I 
tried to get Linux acquainted with my Treo 600. 
Ubuntu (or especially Gnome-Pilot) just doesn't recognize the handheld.
What's strange: my old Palm m125 works without any problems and syncs with evolution just fine.

Here are the messages from the Syslog:

1. Syncing the m125 (after configuring it in evolution to sync just the - 
empty - datebook): 

Dec 14 14:09:25 Workstation kernel: [] usb 3-1: 
new full speed USB device using uhci_hcd and address 3
Dec 14 14:09:25 Workstation kernel: [] usb 3-1: 
configuration #1 chosen from 1 choice
Dec 14 14:09:25 Workstation kernel: [] visor 3-1:1.0: 
Handspring Visor / Palm OS converter detected
Dec 14 14:09:25 Workstation kernel: [] usb 3-1: 
Handspring Visor / Palm OS converter now attached to ttyUSB0
Dec 14 14:09:25 Workstation kernel: [] usb 3-1: 
Handspring Visor / Palm OS converter now attached to ttyUSB1
Dec 14 14:09:30 Workstation kernel: [] usb 3-1: USB 
disconnect, address 3
Dec 14 14:09:30 Workstation kernel: [] visor ttyUSB0: 
Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Dec 14 14:09:30 Workstation kernel: [] visor ttyUSB1: 
Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Dec 14 14:09:30 Workstation kernel: [] visor 3-1:1.0: 
device disconnected


2. Connecting the Treo, pressing the Hotsync-button and waiting for the 
handheld to give up:

new full speed USB device using uhci_hcd and address 4
Dec 14 19:55:46 Workstation kernel: [] usb 3-2: 
configuration #1 chosen from 1 choice
Dec 14 19:58:03 Workstation kernel: [] usb 3-2: USB 
disconnect, address 4

No surprise that GPilot doesn't find any Treo when told to request infos from a new PDA...

lsusb sees the Treo: 
Bus 003 Device 010: ID 0830:0300 Palm, Inc. 
but doesn't identify it, as it does with the m125:
Bus 003 Device 011: ID 0830:0040 Palm, Inc. m125

Both handhelds (and the cradles/cables used for the tests above) work fine with Palm-Desktop under WinXP and Win2K.

...and BTW: the Treo is one of the first series, still from Handspring and gets identified as "Handspring Handheld" by Windows.

Any ideas?

Thanks
Axel

---

### Post by vgrisham on 2008-12-15
Does your Treo run Windows Mobile or Palm OS (Access)?

FWIW, I don't sync at all anymore. Almost all of the software available at Palm's website can be sent straight to your phone. There is an application called TealBackup that will backup all or some of the info on your phone to your SD card. I know that doesn't solve your problem, but I thought I'd throw it out there.

---

### Post by ortenauer on 2008-12-15
> **vgrisham said:**
> Does your Treo run Windows Mobile or Palm OS (Access)?
FWIW, I don't sync at all anymore. [...] backup all or some of the info on your phone to your SD card. I know that doesn't solve your problem, but I thought I'd throw it out there.

This is a *REAL* Palm. so it runs Palm OS 5 :-)
I'm using VFSBAckup to do backups and installing software can be done via GSM, the card reader or my netbook running WinXP - but I used to download various news sites every morning with Plucker and put them on the palm to read while commuting and this was done nearly automatically. I don't want to do that manually every morning - just let it work while dressing, pick up the handheld, shutdown the PC and leave...
I'd also like to put all my contacts into Evolution and don't see any other way than syncing them.
And last but not least: this is supposed to work, so accepting that it doesn't just isn't an option :-))

Regards,
Axel

---

### Post by vgrisham on 2008-12-15
I'll give it a try as well and see if it works in Intrepid with my Centro.

---

### Post by ortenauer on 2008-12-15
One more info that doesn't seem to help:

As seen on... 

               [http://home.arcor.de/ortenauer/powerless.png](http://home.arcor.de/ortenauer/powerless.png)

...device manager tells me there's "Insufficient power to run USB device" ?!

I have run an external 2.5" (USB-powered) HDD on this bus without attaching the second USB cable, so can't imagine there really is a problem with the power...

Clueless
Axel

---

### Post by vgrisham on 2008-12-15
Are you going through a USB hub, or is this a USB port that is attached directly to the motherboard? For a while, I couldn't get my phone to work when attached to the USB ports on the front of my PC, which are essentially a hub.

---

### Post by ortenauer on 2008-12-15
> **vgrisham said:**
> Are you going through a USB hub, or is this a USB port that is attached directly to the motherboard? For a while, I couldn't get my phone to work when attached to the USB ports on the front of my PC, which are essentially a hub.

I've tried both - and I've switched the ports of the two cradles - the Treo didn't work at the port the m125 synced 5 minutes before. But maybe I'll check the connection with the Ubuntu Live-CD on some machines in the office just to be sure. There should be a power supply for the USB-Hub somewhere - if I only knew which one of the dozen lying around here it is :-)

Exhausted (It's 11 p.m. here)
Axel

---

### Post by vgrisham on 2008-12-21
Hey ortenauer,

Sorry for the delayed response. I've tried, but I can't replicate the problem that you're having. My Centro syncs well with both my 32-bit laptop and my 64-bit tower, both running Intrepid (gnome).

---

### Post by ortenauer on 2008-12-22
> **vgrisham said:**
> Hey ortenauer,

Sorry for the delayed response. I've tried, but I can't replicate the problem that you're having. My Centro syncs well with both my 32-bit laptop and my 64-bit tower, both running Intrepid (gnome).

...whereas the Treo doesn't sync here even with an external AC-adapter connected to the hub. Strange...could the different connector (older -Handspring- Treos don't have the universal connector the Palm m125 has and Palm used for Treos since the 650) cause this difference? 

For now I think I'll transfer the data to the m125 using WinXP and from there to evolution. After christmas I'll start looking for a newer Treo or Centro on eBay :-)

CU (and thanks!)
Axel

---

### Post by vgrisham on 2008-12-22
If I wasn't under contract, I'd give you my Centro. I really want an Android G1.

---

### Post by ortenauer on 2008-12-23
> **vgrisham said:**
> If I wasn't under contract, I'd give you my Centro. I really want an Android G1.

Same here - but the G1 was announced here in Germany on Dec., 12, cannot be ordered yet, prices are unknown but can be guessed, as will be sold exclusively by T-Mobile, and they sold the IPhone for app. 75$ with an obligatory contract for 24 months at > 40$/month...:-( 
I'm not ready yet to sell the house to finance my phone :-)

CU
Axel

---

