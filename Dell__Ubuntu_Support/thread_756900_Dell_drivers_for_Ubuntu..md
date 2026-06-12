---
title: "Dell drivers for Ubuntu."
date: 2008-04-16
forum: Dell  Ubuntu Support
---

### Post by benzin24 on 2008-04-16
Hello all, I thought I'd come here of all places, as I saw Ubuntu in action the other day on a friend's computer, and I downloaded the OS myself and burnt it.

All I need help with is finding the Drivers for my Dell Inspiron 1300, I've heard that my GMA and some other things are supported, but I came here to make sure, and see if anyone can help me find the right drivers.
I've spent a couple of hours now looking for some, but to no avail.

My driver needing parts are these:
_Graphics_
Mobile Intel(R) 915GM/GMS, 910GML Express Chipset Family

_Sound_
Sigmatel High Definition Audio CODEC

_Network_
Dell Wireless 1370 WLAN Mini-PCI card

I'm not sure whether I need any other drivers, but these are the crucial ones I think, I'd be eternally grateful if someone could confirm that this hardware is supported, and if so, drivers are available for Ubuntu.

---

### Post by notwen on 2008-04-16
Have you tried running a session off the LiveCD?  Pop it in and see what works and what doesn't.  Your Intel graphcis should work w/o any issue, as should your Sigmatel audio.  Your wireless card is probably a Broadcom as, most Dell cards are, and will likely have issues.  You may want to verify w/ someone w/ more experience dealing w/ Broadcom wireless.  I know some work pretty good using ndiswrapper, but I cannot verify whether or not your specific card works well or not.  

2 out of 3 ain't bad, pop in the LiveCD and see for yourself how well things are running.  Post back and let us know what you find out.  =]

---

### Post by benzin24 on 2008-04-16
Well. this probably should have gone into the absolute beginners forum now I look at it. I haven't actually installed Ubuntu I should have cleared up.

Yes my networking device is a Broadcom.

But I used the boot CD I burned, got to the splash screen, chose the install option, but when I press enter, my HDD whirrs, but nothing happens. Maybe I need to burn a new CD or something, or maybe I'm doing something wrong.

---

### Post by notwen on 2008-04-16
What iso did you download?  You should hit the LiveCD session, where you can use your PC running the Ubuntu OS strictly off the CD and RAM.  From here you can choose to install Ubuntu by double-clicking on the Install icon.

---

### Post by benzin24 on 2008-04-16
I downloaded erm...an .iso called "ubuntu-7.10-desktop-i386.iso" if that helps. I don't know if the LiveCD is different.

Sorry for being a bit of a burden, I'm rather new when it comes to Ubuntu I'm afraid, I should really put this in absolute beginners.

---

### Post by notwen on 2008-04-16
> **benzin24 said:**
> I downloaded erm...an .iso called "ubuntu-7.10-desktop-i386.iso" if that helps. I don't know if the LiveCD is different.

Sorry for being a bit of a burden, I'm rather new when it comes to Ubuntu I'm afraid, I should really put this in absolute beginners.

Np at all. =]  Sounds like you have the right image downloaded.  When the options come up check the disc for errors.  If there are no errors, we'll try something using this LiveCD, before I have you download the alternative install CD.

---

### Post by benzin24 on 2008-04-16
I click "Check disc for errors" it does the same thing, noise, then it just leaves me to select an option again.

---

### Post by notwen on 2008-04-16
> **benzin24 said:**
> I click "Check disc for errors" it does the same thing, noise, then it just leaves me to select an option again.

Never heard this one before, are you able to try this LiveCD in another machine?  If anything the CD itself should be able to check itself for errors.

---

### Post by benzin24 on 2008-04-16
Checking.

---

### Post by benzin24 on 2008-04-16
It looks like the disc doesn't work, tried it on my desktop PC and does the same thing, just does nothing when I choose any of the options.

---

### Post by notwen on 2008-04-16
Are you familiar w/ checking a file's md5sum?  Check [here]("https://help.ubuntu.com/community/HowToMD5SUM") for more info.  Verify you have all of the .iso

---EDIT---
Once you verify your file is in tact, burn it using a slower speed. (8x or less)

---

### Post by benzin24 on 2008-04-16
Well I checked, the iso is in order according to the program I downloaded, I burnt it at 4x to be sure, and I still get the same problem, Laptop and Desktop.

---

### Post by notwen on 2008-04-16
All I can think of is to try the [alternative install CD]("http://www.gtlib.gatech.edu/pub/ubuntu-releases/gutsy/ubuntu-7.10-alternate-i386.iso"), this however won't let you enjoy a live session to see what hardware works and doesn't work.  Not sure what else to recommend w/o you just installing using the alternative install CD.  =\

---

### Post by onefunk on 2008-04-16
hey there

did you try changing the boot sequence on your dell?

try booting directly from the cd

---

### Post by benzin24 on 2008-04-17
> **onefunk said:**
> hey there

did you try changing the boot sequence on your dell?

try booting directly from the cd

Done beforehand :) 

I downloaded the alternate CD, chcked the md5 hash on it, matched up, burnt it at 4x, started installing fine, but one of the files was corrupt, so I'm going to try using a different computer to burn it before I dismiss the notion completely.

---

### Post by notwen on 2008-04-17
Lol, it seems your current PC does not want Ubuntu to get burnt.  Post back and keep us updated.  =]

---

### Post by benzin24 on 2008-04-17
I downloaded Kubuntu instead, got the LiveCD to work, now I'm at the stage where I have to do some sort of root file system in the installation, I've got my main partition and my partition for the SWAP file, how do I make this root file system?

---

### Post by notwen on 2008-04-17
> **benzin24 said:**
> I downloaded Kubuntu instead, got the LiveCD to work, now I'm at the stage where I have to do some sort of root file system in the installation, I've got my main partition and my partition for the SWAP file, how do I make this root file system?

Are you wanting to keep your data and system data seperate?

Example System (80GB HDD)
/ - 15 GB (10GB is generally big enough)
/home - 64 GB (user accounts will share this to store their data)
swap - 1 GB

You would need to partition your HDD to your liking size wise and specify the mount points( / & /home ) for each partition.

---

### Post by benzin24 on 2008-04-17
Good news, Kubuntu is up and running, video and sound drivers running well respectively. All I need now is networking drivers and I'm sorted.

---

### Post by benzin24 on 2008-04-17
Right, I've found a way to get my network drivers up and running, but my Laptop with Kubuntu on won't detect my memory stick, do I need USB drivers? Or to enable them or something?

---

