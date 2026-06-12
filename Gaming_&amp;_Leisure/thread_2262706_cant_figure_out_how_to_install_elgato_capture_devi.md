---
title: "cant figure out how to install elgato capture device"
date: 2015-01-26
forum: Gaming &amp; Leisure
---

### Post by reaper2015 on 2015-01-26
new to linux but was told it is better for gaming then windows, however i have hit a snag i cant get my elgato game capture to work 
[https://www.elgato.com/uk/gaming/gamecapture-hd](https://www.elgato.com/uk/gaming/gamecapture-hd)

as i say im new (taken me a few hours to wrestle with a few other apps (if i have to enter my password in one more time im going to scream!) so forgive me if i have missed something blatent, just want to get my game cap working.

---

### Post by Bucky Ball on 2015-01-26
*Thread moved to **Gaming & Leisure**.*

Welcome. You may have more success here.

Linux better for games than Windows? As the majority of games are made to run natively on Windows, doubt this is the case. You can run some games using Wine and Steam, but certainly not all. Some run great on Wine, others are clunky, some won't install at all.

Software for the Elagato appears to be for either Windows or Mac. Unsure how you would communicate with it without that software. Plug it in then immediately open a terminal and:

```
dmesg
```

Do you see any info at the end of that output that shows the device has been recognised? Does it plug in via USB? Then also try:

```
lsusb
```

... and see if it shows. Does it appear in the file manager? I'd probably stick with Win for the device as the only way to control it, it seems, is via its own software. You may be able to install that software via Wine. Unsure.

---

### Post by reaper2015 on 2015-01-27
> **Bucky Ball said:**
> *Thread moved to **Gaming & Leisure**.*

Welcome. You may have more success here.

Linux better for games than Windows? As the majority of games are made to run natively on Windows, doubt this is the case. You can run some games using Wine and Steam, but certainly not all. Some run great on Wine, others are clunky, some won't install at all.

Software for the Elagato appears to be for either Windows or Mac. Unsure how you would communicate with it without that software. Plug it in then immediately open a terminal and:

```
dmesg
```

Do you see any info at the end of that output that shows the device has been recognised? Does it plug in via USB? Then also try:

```
lsusb
```

... and see if it shows. Does it appear in the file manager? I'd probably stick with Win for the device as the only way to control it, it seems, is via its own software. You may be able to install that software via Wine. Unsure.

dmesg dumps a ton of text but i see

```
[    2.659620] usb 2-6.3.2: Product: GameCapture HD
[    2.659621] usb 2-6.3.2: Manufacturer: Elgato
[    2.659624] usb 2-6.3.2: SerialNumber: 110A2C20FD
[    2.730814] usb 2-6.3.3: new high-speed USB device number 5 using ehci-pci
[    2.772973] random: nonblocking pool is initialized
[    2.811273] EXT4-fs (sdc6): mounted filesystem with ordered data mode. Opts: (null)
[    2.824400] usb 2-6.3.3: New USB device found, idVendor=05e3, idProduct=0608
[    2.824403] usb 2-6.3.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0


```

a good sign no doubt!

lsub gives me:
```
Bus 002 Device 004: ID 0fd9:0051 Elgato Systems GmbH 
```

so ubuntu sees it and knows what it is, so how do we use it? im assuming the default software is out of the window

also yeah learning fast ubuntu is not good for gaming (though kerbal space project is supposed to run better on ubuntu then windows so may just dual boot, once i figure out how to set up my gpu lol(not asking that as i havent searched for that yet))


****edit*****

I tried the linux version of OBS which on windows can use the elgato with out issue....on ubuntu it cant see it, this may simply be a driver issue ofcourse, but then where do i get a ubuntu driverfor it...and do i need one if it was detected in full detail above? ubuntu is very user unfriendly in these cases


*****edit2*****
elgato have said there is no official support for ubuntu.... hmmm im guessing that means i need to wipe ubuntu and re-install windows, hoping im wrong, though one idea, if its just for game capture and streaming then could i get away with a virtual machine running inside ubuntu that runs just windows and the capture software?

---

### Post by Bucky Ball on 2015-01-27
> **reaper2015 said:**
> so ubuntu sees it and knows what it is, so how do we use it? im assuming the default software is out of the window

Running natively in Ubuntu? Yes. 

> **reaper2015 said:**
> ... though one idea, if its just for game capture and streaming then could i get away with a virtual machine running inside ubuntu that runs just windows and the capture software?

This is a possibility, but I'm thinking the game would also need to be running in the virtual machine (though I could be wrong), and gaming in a Win virtual machine does not always give a satisfactory experience from what I've picked up reading other posts on this forum (not a gamer at all, but have learnt a bit about gaming in Ubuntu from others here ... this place is good like that!).

Just a quick tip about the vid card, and you should post a new thread if you need help with that; do an update and check 'Additional Drivers' (might be 'Hardware Drivers' in your install). There may be a driver offered there.

---

### Post by reaper2015 on 2015-02-01
> **Bucky Ball said:**
> Running natively in Ubuntu? Yes. 



This is a possibility, but I'm thinking the game would also need to be running in the virtual machine (though I could be wrong), and gaming in a Win virtual machine does not always give a satisfactory experience from what I've picked up reading other posts on this forum (not a gamer at all, but have learnt a bit about gaming in Ubuntu from others here ... this place is good like that!).

Just a quick tip about the vid card, and you should post a new thread if you need help with that; do an update and check 'Additional Drivers' (might be 'Hardware Drivers' in your install). There may be a driver offered there.

The game runs on my main pc or ps4, hmmm i guess i should explain a bit better.

pc / ps4
\/
hdmi cable 
\/
elgato capture hd ---> hdmi-----> TV
\/
usb
\/
ubuntu laptop 

so whats happening is the pc plays the game, the signal is sent via hdmi to the elgato, which sends the image to my tv and a usb signal to the attached laptop, this means i can record games in 1080p with zero effect on the pc, all recording/streaming is delt with on the laptop. Back when i ran windows this worked perfectly.

I contacted elgato customer care who stated they do not support linux only mac and windows, so no help there.

after many many rough starts i got windows 8.0 running in a vmware player, i installed the capture card software in that virtual machine and it works....sort of, at random the picture will break up and from what i can tell the virtual machine only sees one core of the processor. 

i view this as a work around NOT a solution. 

Im out of ideas so it looks like when i get some free time i will need to ditch ubuntu and switch back to windows, its a shame as i have everything else setup perfectly and love how fast it starts up etc but i need to use my capture device and despite it being a very common device thier appears no linux 3rd party support for it at all

---

### Post by Bucky Ball on 2015-02-01
Yes, a pity, but nothing to do with Linux or Ubuntu. If third-partys don't support Linux, not a lot can be done apart from one of the community getting one of these devices and pulling it apart or attempting to work out how they've been programmed and set up.

What I normally do is email the manufacturer and ask why they don't support Linux and letting them know I will be buying hardware that does and I can't support them in the meantime.

Good luck in your endeavours whichever way you decide to go. Dual-booting is your only other option (perhaps game on Windows and do the rest on Ubuntu). ;)

---

