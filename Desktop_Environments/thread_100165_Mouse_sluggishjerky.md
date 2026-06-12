---
title: "Mouse sluggish/jerky"
date: 2005-12-07
forum: Desktop Environments
---

### Post by pr0fess0r on 2005-12-07
Hi
I just set Ubuntu up on a dual P3 500MHz machine with 392MB RAM. The install went fine but the USB mouse and keyboard were very sluggish - I change them both to PS/2 and the keyboard is fine, but the mouse is still very sluggish and unresponsive. I'm wondering if itmight be conflicting with other hardware (I have a network and 802.11g PCI card in the box too, and an ATI Radeon 9800SE graphics card). I've monitored performance and the CPU and RAM aren't maxing.. what's the best way to track down the problem - are there logs or settings I can adjust or examine?
Many thnaks in advance!

Lucas

---

### Post by r4ik on 2005-12-07
Give the machine a hard reset with usb plugged in.
Worked for me try it.

---

### Post by tgranny on 2005-12-07
I am having a similar problem with my mouse on a dual processor machine with ubuntu 5.10.  In my case, it's a dirt common Logitech usb optical mouse on a dual PIII-800, Tyan Tiger mobo with a VIA chipset, GeForce4 Ti4600, yada yada yada.

Barebones Breezy installed straight from media without incident;  When it was finished, gdm smiled brightly at me and I logged in.  Everything worked perfectly except the mouse moved around rather choppily.  Upgraded kernel to 2.6.12-10-686-smp and did the requisite upgrade from "nv" to "nvidia".  Mouse still slow and not very responsive.

I have tried swapping (nearly) identical mice with my working uni-processor Breezy and Hoary desktops, I've tried plugging the mouse into other USB holes (only one 1.1 uhci on this machine), I have tried using a PS/2->USB adapter (to try to remove the USB from the equation), I've restarted hotplug, I've followed the template xorg mouse configs [1], I've tried pumping values into /sys/module/usbhid/parameters/mousepoll, ctrl-alt-bksped and rebooted until I can stand to no more ... no dice... the mouse is always there, functional but always sluggish.  I've even tried nuking-and-paving the machine and installing 5.04 to see if that solved the problem.  The mouse doesn't work at all in Hoary on this machine.

I have looked around on these forums for the past few days and have found nothing to remedy this problem so far.  The closest I've found were:

[1] [http://ubuntuforums.org/showthread.php?t=99469&highlight=mouse](http://ubuntuforums.org/showthread.php?t=99469&highlight=mouse)
[2] [http://ubuntuforums.org/showthread.php?t=100089&highlight=mouse](http://ubuntuforums.org/showthread.php?t=100089&highlight=mouse)

It's interesting to note that pr0fess0r's machine doesn't have nVidia so it's not related to the graphics card--all the fancy graphics stuff and such seems nice and worky to me here.

Now, I did, however, discover something rather interesting about the problem the other day.  I decided to dump a bunch of files to this machine over the network (so I could back them up and upgrade my good desktop to Breezy, incidentally) and I noticed that the mouse performance shot up to "almost normal" during the time there was lots of I/O going on.  I don't yet know if this is related to high load or just plain I/O activity.

Also, could be significant... I also noticed that /proc/interrupts looks like this on the dual-cpu machine (Breezy):

           CPU0       CPU1
...
 19:       3947       3900   IO-APIC-level  uhci_hcd:usb1, eth0
...

and this, on the uni-processor Hoary machine (running 2.6.10-5-686, Intel instead of VIA chipsets):

           CPU0
...
  9:    4776158          XT-PIC  uhci_hcd, eth0, ohci1394
 10:    3470205          XT-PIC  uhci_hcd
...

Could this be an APIC or BIOS problem?

---

### Post by tgranny on 2005-12-07
My meese are both Logitech, USB, 3-button scrolly jobbies.  One was badged on the box as "USB and PS/2" (came with a little green doingly adapter thingy) and the other was just plain "USB".

The part numbers are "M/N M-BJ58; P/N 830524-0000" and "M/N M-UV96; P/N 831139-1000".

I should also note that I have tried both meese on my uni-cpu and dual-cpu desktops and the problem does not follow the mice when they change machines.

Neither mouse presented a problem in Debian, Gentoo, Slackware, RedHat or that other operating system--it's this damn dual that's the problem.  Probably wonky VIA support or something similarly frustrating.

---

### Post by pr0fess0r on 2005-12-07
Hi

This is my /proc/interrupts

           CPU0       CPU1
  0:   10032675    9397506    IO-APIC-edge  timer
  7:          0          0    IO-APIC-edge  parport0
  8:          0          1    IO-APIC-edge  rtc
 14:      36790      34805    IO-APIC-edge  ide0
 15:      88741      85057    IO-APIC-edge  ide1
 17:       5568       5381   IO-APIC-level  Ensoniq AudioPCI
 18:      19664      19784   IO-APIC-level  uhci_hcd:usb1, eth0
 19:      49992      50008   IO-APIC-level  eth1
 20:          0          0   IO-APIC-level  acpi
NMI:          0          0
LOC:   19428710   19428722
ERR:          0
MIS:          0

I also notice the keyboard can be very slow and can miss letters - I have to wait for it to catch up with me while typing this. Oddly a couple of times this morning my mouse suddenly decided to work normally for a minute or two then went back to it's sluggish behaviour. I though changing the cpi might help but I dont know how to do this for a non-Logitech mouse. There is device manager key called usb_device.speed_bcd (=336) but I dont know how to change it or if it means anything
Any suggestions appreciated :)
cheers
pr0fess0r

---

### Post by tgranny on 2005-12-07
I've installed ubuntu on 5 other machines so far and I never had to fight with getting the mouse to work.  That just seems somehow wrong to me.

I refuse to frobnicate the wang doodles just to get things to work properly.  Yes, the problem might go away if I recompile the kernel myself.  Yes, the problem might go away if I play with some widget or slidy bar thing.

If I'm stubborn enough, and get some help from others with the same problem (thank Dog for the forums), we might find a solution to this and contribute something back to the community.

Things just work with ubuntu and I don't (normally) have to fight with anything or spend endless hours tweaking everything--that's part of why i like it so much.  My debian dev friends just look at me funny now but at least it got my wife using a real OS.  I'll just have to wait now until I get the mouse working on this machine before I can "borrow" her laptop is all.

But I digress...

Anyway, in the interests of coming up with a solution to this problem, here's a more detailed account of the hardware in this machine:

(from "lspci")
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev
30)
0000:00:10.0 Unknown mass storage controller: Promise Technology, Inc. PDC20268
(Ultra100 TX2) (rev 02)
0000:00:12.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:12.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:00:13.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
0000:00:14.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a2)

(from "lsusb")
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

(from "free")
             total       used       free     shared    buffers     cached
Mem:       1556336    1524180      32156          0       3396    1346336
-/+ buffers/cache:     174448    1381888
Swap:      1220900      12540    1208360

---

### Post by tgranny on 2005-12-07
I've installed ubuntu on 5 other machines so far and I never had to fight with getting the mouse to work.  That just seems somehow wrong to me.

I refuse to frobnicate the wang doodles just to get things to work properly.  Yes, the problem might go away if I recompile the kernel myself.  Yes, the problem might go away if I play with some widget or slidy bar thing.

If I'm stubborn enough, and get some help from others with the same problem (thank Dog for the forums), we might find a solution to this and contribute something back to the community.

Things just work with ubuntu and I don't (normally) have to fight with anything or spend endless hours tweaking everything--that's part of why i like it so much.  My debian dev friends just look at me funny now but at least it got my wife using a real OS.  I'll just have to wait now until I get the mouse working on this machine before I can "borrow" her laptop is all.

But I digress...

Anyway, in the interests of coming up with a solution to this problem, here's a more detailed account of the hardware in this machine:

(from "lspci")
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev
30)
0000:00:10.0 Unknown mass storage controller: Promise Technology, Inc. PDC20268
(Ultra100 TX2) (rev 02)
0000:00:12.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:12.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:00:13.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
0000:00:14.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a2)

(from "lsusb")
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

(from "free")
             total       used       free     shared    buffers     cached
Mem:       1556336    1524180      32156          0       3396    1346336
-/+ buffers/cache:     174448    1381888
Swap:      1220900      12540    1208360

---

### Post by pr0fess0r on 2005-12-07
Let's hope someone can help out and resolve this for us and future users :)

---

### Post by tgranny on 2005-12-07
Well, maybe we can narrow down the hardware issues.

Here are a few points:

1.  It seems that there's not a lot of people seeing this problem ("mouse works fine but is hideously slow and otherwise machine is fab") so this must be somewhat a rare problem and/or our respective machines are.

2.  We both have dual-P3 boxes so it's possible the problem is related to dual-cpu somehow.  However, I also saw this same problem with the stock 5.10, non-SMP, 2.6.12-10-{386,686} kernels.

3.  We both have different video cards.  My graphics performance seems fine.  This problem is not the typical "everything/graphics slow" type of problems.

4.  Lack of swap or free mem does not seem to be at fault here.

5.  I have done a clean reinstall from bare metal on this box and the problem persists so it's very easy for me to reproduce this.

6.  Mouse performance improves when the system is performing lots of I/O operations using the 2.6.12-10-686-smp kernel (like scp'ing several gigs of files across the LAN, as an example).

7.  We've both got different sound cards.  It's likely that this isn't related but is worth mentioning here for completeness.

8.  I'm seeing almost the exact same /proc/interrupts output as you are.

---

### Post by pr0fess0r on 2005-12-07
That all makes sense. I also find the keyboard to be sluggish as well, and wehn typing in long posts, sometimes it'll start missing out letters like "i" for no reason! This morning I was messing around and a couple of times my mouse suddenly came right, working smoothly for a minute or so, then back to slug mode again. 
When I installed my box the non-SMP kernel was running by default, I downlaoded the SMP version and the box appears a little faster but the mouse problem hasnt changed (and it seems to be the same regardless of whether you use USB or PS/2)
very wierd...

---

### Post by tgranny on 2005-12-07
Can't say I found the keyboard cutting out on me like you have but I did see the same problem with the mouse regardless of whether it was plugged into the USB port or the PS/2 port.

I didn't see any improvement when using the PS/2->USB adapter plug so I just put the mouse back on USB like it is on my working desktop.

---

### Post by tgranny on 2005-12-08
Does silence mean that nobody else has this problem?  Are all my previous assertions wrong?  Am I even close?  Does anybody at least have any suggestions about what I might try or look at next?  I'm out of ideas.

I doubt just building a new non-stock kernel for myself will solve this problem.  The mouse works--it's just slow (unless I'm copying lots of files over the network).  I don't know enough about APIC or whatnot to debug this on my own.

I could poke my way through logs but I don't even know if I'll find something that says why things aren't working they way they ought to work.  I could spend my time digging around and comparing assorted things to my working breezy desktop but I don't have any real idea what to focus on.

It doesn't seem to be related to video or USB because I think I can eliminate those from the equation.  It does seem to be related to dual-CPU machines but not to the stock SMP kernel.

---

### Post by pr0fess0r on 2005-12-08
My thoughts exactly. Hopefully someone can point us in the direction of a log or script or parameter. Ubuntu is working beautifully for me except the mouse is so awkward to drag around the screen it really ruins the experience. I thought Linux was all about logs and openness and I'd be surprised if there wasnt a way we could track this problem down...

---

### Post by tgranny on 2005-12-14
Well, for what it's worth, booting with the "noapic" kernel option seems to do the trick on my machine here.

Thanks to all who replied.

---

### Post by pr0fess0r on 2005-12-14
Hi
Brilliant! it's fixed
I followed the instructions at [http://ubuntuforums.org/archive/index.php/t-75281.html](http://ubuntuforums.org/archive/index.php/t-75281.html) which has more details on the process. Oh happy day :) Thanks tgranny!

---

### Post by dvstin on 2007-02-20
I've had the problem of a jerky mouse, and I find that this fixed it:

open a terminal window somehow (either tty1 or a terminal emulator or ssh from another machine)

sudo rmmod usbhid ; sudo modprobe usbhid

The problem goes away when toggling this module, so I think it could be related. Maybe usbhid should be a keyword for this thread. I still don't understand the source of the problem and adding kernel boot options seems like a hack-workaround not actually determining and fixing the problem.

I am using ubuntu 6.10

---

