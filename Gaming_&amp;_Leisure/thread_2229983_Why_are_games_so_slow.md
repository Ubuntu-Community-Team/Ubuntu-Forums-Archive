---
title: "Why are games so slow?"
date: 2014-06-16
forum: Gaming &amp; Leisure
---

### Post by weisswolf on 2014-06-16
Okay so I just installed Ubuntu, P.S. I am not new because I had it on an older computer.
And everything was really quick on Windows 8, now I can barely play any games.
I have an Intel I5 Core and 8GB RAM. Anything useful will really help.
Games are slow like, Starbound, Minecraft, Gmod, L4D2, and Don't Starve.
They are all on the fastest settings, plus I am on a laptop and it is bad framerate
MY GLMARK2 IS SO LOW... It is 182!!! And it is supposed to be 1200.

-PCI Devices-
Host bridge        : Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
VGA compatible controller        : Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
USB controller        : Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
Communication controller        : Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
USB controller        : Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
Audio device        : Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
PCI bridge        : Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
ISA bridge        : Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
SATA controller        : Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
SMBus        : Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
Network controller        : Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)


Thanks in advance, and I appreciate replies, you can still send me them because I will have Ubuntu as a side OS but I am reinstalling Win 8 soon! But that is in a month so I would appreciate replies.
Thank you all, but I want to fix it so bad, because my computer cost about 1000$ and I don't want to spend 100$ for Win 8. I am going to try to play on Fedora and OpenSUSE and see if that works.

EDIT: I have fixed it! I reinstalled Ubuntu and this time did not update the drivers and now it runs really fast. Thanks for all the help!

---

### Post by Ranko Kohime on 2014-06-16
First off, what games are slow?  And how are they slow?  (low framerates, long loading times, etc)
Is this a laptop?
Are you able to run glmark2?  If so what is the score?

I'm sure others will chime in with different questions that might help pinpoint the problem.

---

### Post by Peter_Solver on 2014-06-16
What kind of hardware do you have? How are you running the games? I think you may want to try removing your game graphic settings to make your games run faster.

---

### Post by mastablasta on 2014-06-17
they described the hardware: 
Intel I5 Core and 8GB RAM
Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

those games should run well on this setup. i run them on a much much weaker PC. intel drivers have issues it seems.

to the OP - try running a different desktop. i am not sure what is causing the slowdown. i have no experience with intel GPU. i know that they use opensource drivers that can be upgraded to latest or dev version using a PPA. perhaps that would help?

---

### Post by weisswolf on 2014-06-17
I have updated the drivers and used a desktop that reduced my cpu usage to 1% while not using anything... Still can barely play OpenArena without lag...
I am going to get a windows 8 install disc soon, I want my fast computer back.

---

### Post by mastablasta on 2014-06-17
one thing here - is there any other GPU inside?

interesting though intel doens't have good chips but the one one your mashcine should be able to handle these games.

one thing to try and see is if enough ram is set aside for the GPU.

other than that - use Windows if it works well :)

---

### Post by oldrocker99 on 2014-06-17
You are free, OP, of course, to go back to a closed-source, porous, vulnerable OS, but you should at least try to solve your gaming problem before throwing your hands up and heading back to the M$ fold.

---

### Post by Ranko Kohime on 2014-06-19
> **mastablasta said:**
> one thing here - is there any other GPU inside?

interesting though intel doens't have good chips but the one one your mashcine should be able to handle these games.

one thing to try and see is if enough ram is set aside for the GPU.

other than that - use Windows if it works well :)
Intel iGPU's dynamically allocate, and their static RAM usage is usually fixed at 128MB.

And the drivers for Intel are the least hassle, in my experience, so I'm really lost as to why the OP is experiencing this sluggishness.  :(

---

