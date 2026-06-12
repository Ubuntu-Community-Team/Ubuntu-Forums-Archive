---
title: "urgent help please"
date: 2005-03-06
forum: Desktop Environments
---

### Post by raxa on 2005-03-06
Hi there, a friend of mine gave me the cds to install linux, ive using it one day long, yo im crappy at using it, and i have 2 problems, first, i have a lexmark 1100 inkjet printer, and the driver is already installed in linux, but when i send a test page to print it never does it... donno how to solve this problem, second: i have a ess audiodrive sound card but i cant find any drivers for it... help!!!... please? [-o<

---

### Post by Circle of Owls on 2005-03-06
Re: the printer issue- Try installing the Gimp-Print drivers, they have solved the same problem on my Epson 636. Go to System-->Synaptic, then search for and install gimp-print. This thread has some more info: 

[http://www.ubuntuforums.org/showthread.php?t=9230&highlight=Epson+Stylus](http://www.ubuntuforums.org/showthread.php?t=9230&highlight=Epson+Stylus) 

Be sure to switch your printer to the new drivers after installing.

Hope it helps.

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=raxa]Hi there, a friend of mine gave me the cds to install linux, ive using it one day long, yo im crappy at using it, and i have 2 problems, first, i have a lexmark 1100 inkjet printer, and the driver is already installed in linux, but when i send a test page to print it never does it... donno how to solve this problem, second: i have a ess audiodrive sound card but i cant find any drivers for it... help!!!... please? [-o<[/QUOTE]


Don't know about hte printer, but I found this about the sound card:

> 
    The most recent linux kernels and voxware sound drivers automatically use the AudioDrive chips in their 16 bit mode when configured as a SoundBlaster Pro. From the "readme.cards" file which accompanies the latest kernel sources:

ESS ES1688 and ES688 'AudioDrive' based cards
---------------------------------------------
 
Support for these two ESS chips is embedded in the SB Pro driver.
Configure these cards just like SB Pro. Enable the 'SB MPU401 MIDI port'
if you want to use MIDI features of ES1688. ES688 doesn't have MPU mode
so you don't need to enable it (the driver uses normal SB MIDI automatically
with ES688).
 
NOTE! ESS cards are not compatible with MSS/WSS. 

From here:

[http://www.gweep.net/~sfoskett/hardware/audiodrive.html](http://www.gweep.net/~sfoskett/hardware/audiodrive.html)

worth a shot.

---

