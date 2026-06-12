---
title: "Problem booting ubuntu 9.10 on Dell Dimension 2400"
date: 2009-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by smoses on 2009-11-22
I just installed ubuntu 9.10 on a Dell dimension 2400 machine and I'm having problems during boot time. I can't get the machine to boot unless I press F12 to go to the boot device menu and either select the first highlighted option "Normal" or the second option "Hard-Disk Drive C:" or the third option "System setup". I get a blank screen if I don't press F12 when I start the machine and it freezes shortly afterwards. It doesn't respond to any button press and even the "Num Lock" led on the keyboard doesn't toggle on and off when I press the NumLock button, it feels like the machine is dead.

I can change the boot sequence on the setup menu as well (by pressing F2 when I turn on the machine) but that doesn't solve the problem.

There is no other OS installed on this machine.

Any idea how can I get this machine to boot without going throuth the boot menu?

---

### Post by RedRat on 2009-11-22
> **smoses said:**
> I just installed ubuntu 9.10 on a Dell dimension 2400 machine and I'm having problems during boot time. I can't get the machine to boot unless I press F12 to go to the boot device menu and either select the first highlighted option "Normal" or the second option "Hard-Disk Drive C:" or the third option "System setup". I get a blank screen if I don't press F12 when I start the machine and it freezes shortly afterwards. It doesn't respond to any button press and even the "Num Lock" led on the keyboard doesn't toggle on and off when I press the NumLock button, it feels like the machine is dead.

I can change the boot sequence on the setup menu as well (by pressing F2 when I turn on the machine) but that doesn't solve the problem.

There is no other OS installed on this machine.

Any idea how can I get this machine to boot without going throuth the boot menu?

HOw old is this machine?? I had one of these years and years ago. Tell us a little bit about your hardware, i.e., processor and speed, how much memory, graphics card, etc. If I recall correctly, the old 2400 came with 256Mb memory that could be upgraded maybe to 512 Mb but I don't know for sure. If I remember correctly, it used a Pentium III processor.

---

### Post by smoses on 2009-11-23
Thanks for your prompt reply, this machine is around 8-9 years old. Its got a P4 2.66GHz processor, 256MB DDR SDRAM, and 82845G chipset.

---

### Post by RedRat on 2009-11-23
> **smoses said:**
> Thanks for your prompt reply, this machine is around 8-9 years old. Its got a P4 2.66GHz processor, 256MB DDR SDRAM, and 82845G chipset.
My guess is that you might just not have quite enough memory. If possible, you might want to buck this up to at the very least 512Mb and higher if possible. If this is not possible for your machines, you might want to try a lighter weight Ubuntu, e.g., Xbuntu, or PCLinuxOS. I tried PCLinuxOS on my old Dimension and it seemed to work quite well, but that was back in 2006 and I forget what version it was. But my old computer was a tad bit older than yours and I just replaced it with my current Dell 530n.

---

### Post by teward on 2009-11-23
FYI: Machines that are 8-9 years old physically can't hold 1GB of RAM without you spending about $150 to find a stick that will work.

If your computer is still working, I commend you.  However, the specs on it are so old they're way more obsolete than newer operating systems, and especially the newest Ubuntu OS, require.

---

### Post by smoses on 2009-11-24
Fixed it :P:P:P. 

Edited /etc/default/grub
changed     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to              GRUB_CMDLINE_LINUX_DEFAULT="splash"
and ran 'update-grub'

I power cycled the machine and it booted automatically this time without having to go through the boot device menu.

---

### Post by Bosje on 2010-01-09
> **smoses said:**
> Fixed it :P:P:P. 

Edited /etc/default/grub
changed     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to              GRUB_CMDLINE_LINUX_DEFAULT="splash"
and ran 'update-grub'

I power cycled the machine and it booted automatically this time without having to go through the boot device menu.

Hello,
I have exactly the same machine and the same problem... I'm very happy to find your solution! But I am very new to Linux, so please help me out.... how do I edit?
Greetings, 
Rene.

---

### Post by Bosje on 2010-01-09
I figured it out...
praises to the internet and the people on it!
thanks a lot.

---

### Post by besky on 2010-01-18
Okay, and how did you fix it?????

---

### Post by billyboy1995 on 2010-01-26
> **TrekCaptainUSA said:**
> FYI: Machines that are 8-9 years old physically can't hold 1GB of RAM without you spending about $150 to find a stick that will work.
 
If your computer is still working, I commend you. However, the specs on it are so old they're way more obsolete than newer operating systems, and especially the newest Ubuntu OS, require.
Not true. I got two 512mb sticks for 30$ secondhand but work and look like new. They where for the same system too.

---

### Post by mtdesign on 2010-03-10
> **TrekCaptainUSA said:**
> FYI: Machines that are 8-9 years old physically can't hold 1GB of RAM without you spending about $150 to find a stick that will work.

If your computer is still working, I commend you.  However, the specs on it are so old they're way more obsolete than newer operating systems, and especially the newest Ubuntu OS, require.

The Dell Dimension as is comes with the ability to add 2 1GB memory sticks to it, default it has 1 256 stick. I upgraded mine to 2 GB for $35.00. I have though not been able to get anything above 8.04 LTS to work on my Dell Dimension 2400.

---

### Post by capex on 2010-03-12
I have the same problem on the same machine. The ubuntu logo comes up as if its going to boot, and then the blank screen comes up... how do i edit the grub if i can't boot?

---

### Post by zach.detton on 2010-03-14
A problem I sometimes ran into on older machines is the BIOS AV Protection would prevent GRUB from being properly installed to the MBR. I'd have to disable the MBR Protection in the BIOS temporarily until after the OS install or update was complete.

---

### Post by sportscliche on 2010-03-20
I got Xubuntu 9.10 running on a 2003-vintage Dell Dimension 2400 with 512 Mb RAM.  I've installed Ubuntu, Xubuntu, and Kubuntu on various machines in recent months and this Dell desktop was by far the most challenging.  I'll run through what I did in the hopes that others may benefit, although all this may be moot with an impending LTR next month (April 2010).  Maybe all these problems will go away in 10.04.

The first obstacle was the CD/DVD drive.  An Ubuntu 9.10 Live CD that worked well on previous installs with other machines caused the Dell to chronically choke and freeze.  I was setting up for dual boot and confirmed that DVDs/CDs played splendidly on the W2k partition.  I also tried two different Xubuntu 9.10 disks that worked marginally better, but neither Xubuntu CD or the Ubuntu CD could give me a successful install.  I'd eventually get full lock-up at various points in the process -- the furthest I ever got was 80% complete with Xubuntu.  Only a power off/on cycle could unfreeze the computer.

I gave up on the CDs and made a boot disk using a 2 Gb USB flash drive.  Instructions on how to do this are on the Ubuntu wiki:

[https://help.ubuntu.com/9.10/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/9.10/installation-guide/i386/boot-usb-files.html)

but if you have access to another computer running Ubuntu, it's ridiculously easy.  Download the Ubuntu .iso file, put the empty flash drive in a USB port, and run the startup disk creator utility.

To boot off the flash drive, put it in a USB port on the Dell, and reboot into BIOS (hold down key F2).  BIOS will recognize that the USB device is bootable and give you the option to put it first in the sequence.

Before attempting the install, I chose to tryout Xubuntu 9.10 running live on the flash drive and was finally able to see the desktop.  I could navigate around for a while, but eventually it would hang up in a full freeze, requiring a hard reset.  The flash drive, however, was key to getting the installation of Xubuntu 9.10 to run to completion.  I opted for Xubuntu because it has a lightweight interface (compared to Ubuntu/Kubuntu), which puts minimal demands on system resources. I figured it had the best chance of success on the Dimension 2400.

[Note: If you are doing a dual boot, it's always wise to go immediately into your resized Windows partition on the next two boots and allow allow it to run chkdsk.  When you've convinced yourself the Windows side is OK, then boot into Ubuntu.]

My problems were not over.  Rarely could I boot to the Xubuntu desktop as I'd usually get a blank screen lockup before even getting to the splash page.  This problem is addressed in post #6 above.  I got to the terminal by choosing the recovery mode option in GRUB.  From there you can perform the simple edit.  There are various editors available, but I like the onboard program called nano because it is easy to use and navigate.  Edit the offending grub file by entering:

sudo nano /etc/default/grub

at the terminal prompt.  Perform the simple edit and save your changes with Ctrl-X, then run

sudo update-grub

and power cycle.  This fix got me reliably to the desktop.  

At this point I found that Xubuntu would experience an intermittent, unpredictable lockup.  This could occur in Firefox, playing Solitaire, or even with just the screensaver running.  Power cycling was required to clear the computer.  The kernel updates did not cure the problem.  Freeze seemed to occur after a couple of hours or so, certainly enough to be unacceptable.  In addition, I noticed that DVDs were playing poorly, with slightly choppy rendering especially on Movie Player fullscreen.  This is caused by an incompatibility of 9.10 with the Dell's Intel graphics hardware.  The fix can be found here:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Just follow the instructions for `Installing the package'; start with

sudo nano /etc/apt/sources.list

and go from there.  

After reboot, you should find yourself with a screaming fast Xubuntu operating system on the Dimension 2400.  I have been pounding on it for days trying to get it to freeze and it just keeps going.  DVDs now play crisp and clean.  And prepare yourself for startup and shutdown times that are so fast it can be startling.

---

### Post by Slipstick-Joe on 2010-03-20
> **smoses said:**
> Fixed it :P:P:P. 

Edited /etc/default/grub
changed     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to              GRUB_CMDLINE_LINUX_DEFAULT="splash"
and ran 'update-grub'

I power cycled the machine and it booted automatically this time without having to go through the boot device menu.

Congratulations on solving it.

I'm using a Dell Dimension 2400 right now, but with its memory max'ed out to 1 GB.  It runs just fine.  You'll be happier with yours if you can add or replace memory to bring it to at least 512 MB.  Used memory is cheap, and easily installed.  These machines have quite a bit of life left in them.

---

### Post by dolson on 2010-04-10
I have been fighting this issue on this PC for some time... It's weird - it seems if I unplug any PCI devices, it USUALLY boots fine.

I tried the fix mentioned in post 6, no dice.

On top of this, I am trying to get one of two PCI modems to work, because this is a PC for my mother in law - her Windows was dog slow, so I wiped it for her and put Ubuntu on. But man, issues like crazy... I didn't know trying to get dialup working on Ubuntu was such a hassle.

---

### Post by frogging on 2010-05-03
OK to set the record streight.  The Dell Dimension 2400 is P4 runs at 2.2Mhz come with 128mb ram upgradeable to 2gb. OK so now you all know.  

So now I have up graded mine to 512mb 2 256mb sticks $2.00 each.
and I got Ubuntu 9.10 to run.  But I clicked no networks cause it was not running and it was set at connect I hit disconnect and then hit connect again and every thing froze up.

Rebooted and it comes up with GNU GRUB version 1.97~beta4
in the box is 
1 Ubuntu, Linux 2.6.31-14-generic 
2 Ubuntu, Linux 2.6.31-14-generic (recovery mode)
3 Memory test (memtest86+)
4 Memory test (memtest86+, serial console 115200)

OK funny the machine I'm typing this on is a Dell OptiPlex GX115 P3 with 512 ram.  So it should work on the Dell Dimension 2400.

OK so here is what happens if I hit 3 or 4 above it runs a Mem test and tells me my mem is fine.

When I hit 1 from the list above I get this, The ubuntu simble comes up few flickers of the hard drive light and then blank screen.

Reboot 
The ubuntu simble comes up then shows *Starting init crypto disk...                                                  OK
_
and it locks up no more Hard Drive flicker

Reboot again GNU GRUB screen comes up again pick number 2

Whole bunch of stuff comes across screen.  Screen flickers on off 2-3 times then hangs at Skip Stopping firewall: ufw (not enabled)
_

Any Help would be nice
:popcorn::confused:

**** Start edit
Reason for edit forgot something
I can run Knoppix 5.1 Live CD and all works good.  Want to run Ubuntu on the Dell Dimension 2400
**** End edit

---

### Post by sportscliche on 2010-05-07
frogging: Is your problem still with 9.10?  Or the brand-new 10.04?  If 9.10 did you try the fix indicated in post 6 of this thread?

---

### Post by trippap on 2010-05-19
I also have a Dell Dimension 2400 with a Pentium 4 processor, 1GB RAM, and on-board Intel graphics support. I recently installed LinuxMint version 8 (Helena), which runs over Ubuntu, and I experienced system hangups. My symptoms were a cursor I could move on the screen, but everything else was black on the screen, and the only way to recover from the condition was a power-off reboot. I tried updating the Ubuntu kernel to 2.6.32 because some users had reported that fixing the problem, but it did not fix it for me. Yesterday, I was pleased to see that LinuxMint version 9 (Isadora) had been released, so I did a fresh install of it on my machine, wiping out everything on my partition. To my dismay, the problem is even worse with the new version, and the hangups occur with no action or when doing things. This time, the screen goes black and I get an occasional vertical bar pattern near the top of the otherwise black screen. The bars go away, and then come back after 20-30 seconds. It would appear that the system has just crashed and is cycling through memory writing stuff, thus the bars I see on the screen. Again, the only way to break out of the hangup is power-off reboot. I've tried disabling the screen saver and have power management configured to never turn anything off. I expect I'll have to go back and try LinuxMint version 7, because I can't live with these hangups.

---

### Post by sportscliche on 2010-05-20
Trippap: could there be something wrong with your hardware?  Can you boot Mint or Ubuntu from the Live CD?  If so, what happens when you run the system memory check?

---

