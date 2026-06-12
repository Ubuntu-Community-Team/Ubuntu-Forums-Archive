---
title: "Dell dimension 8300 can't detect CD drive"
date: 2010-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by s0563764 on 2010-09-18
Hi

I recently turned my old PC into a living room PC with ubuntu 10.04 to display media on the TV, and to serve media between the computers in the house.

Unfortunately as I was a bit of an ubuntu newbie, tried to find out what the CD drive in my machine was by physically taking it out. After I reattached it to the PATA cable? and power supple, I thought the drive was still functioning, indeed it still opens, but is no longer registered as installed on the computer after I checked the bios.

I was checking the drive because I had a feeling it was somehow locked from reading media from DVDs, though it can read games on DVDs.

Is there anyway for me to determine if it is a hardware issue/ I have connected it back wrong?

---

### Post by mr clark25 on 2010-09-18
did you turn the computer off when you disconnected it?

you might make sure the pata cable is installed all the way.

---

### Post by s0563764 on 2010-09-18
Yeah I turned if off, unplugged it etc.

---

### Post by mr clark25 on 2010-09-18
sounds like the cd drive might have gave up. do you have another one that you can try in it?

also, is it a IDE drive (IDE is sometimes called PATA) or is it a SATA drive? (you sounded a little unsure...)

SATA:
[http://www.cs-electronics.com/images-large/SATA-Signal-Cable-1.jpg](http://www.cs-electronics.com/images-large/SATA-Signal-Cable-1.jpg)

IDE:
[http://www.frontx.com/pro/c203_018p2.gif](http://www.frontx.com/pro/c203_018p2.gif)

---

### Post by s0563764 on 2010-09-18
no its defo a PATA, I wasn't sure if IDE was different, but its no SATA. I'm concerned really because there are bad sectors on the current main HDD, so if it gets worse I would need to install ubuntu on a hard drive, but with no CD drive it may be quite a bit of hassle.

I want to make sure it is not the motherboard PATA port? was the issue. I am quite tempted to replace the drive anyway as the firmware I believe made it struggle with certain DVDs in the first place.

---

### Post by Doulos1 on 2010-09-18
There should be two IDE sockets on the mother board.  Try the other one and make sure all cables are completely inserted into their sockets.

---

### Post by s0563764 on 2010-09-18
cheers, I'm not in the house, but I wasn't sure  about the IDE, because I have only dealt with SATA so far, I'll post back when I'm back in the house.

But out of curiousity is there a way to determine if its the drive of the sockets?

---

### Post by Doulos1 on 2010-09-18
If you have a working hdd on the same cable as the cd player, it is not the socket.  Might be the cable, though.  In that case, try another cable if you have one and make sure everything is plugged in all the way.

---

### Post by s0563764 on 2010-09-21
Hey guys, I have SATA HDD for that computer, I've tried an old (ie 13 year old) CD drive, it did not detect it but it powers up.

I had a look in the bios, it seems it only detects my drive (both of them) if it is a secondary drive master BUT if I enable it I can't boot up. Even if I eliminate from my boot sequence.

Could it just be installing the drive? or I just can't boot up from it?

---

### Post by s0563764 on 2010-09-22
Nevermind guys after some much bios mucking about I managed to get it to boot! Thanks guys

---

### Post by s0563764 on 2010-09-22
I spoke too soon! Enabling it means it takes the computer over 3 mins to boot!

---

