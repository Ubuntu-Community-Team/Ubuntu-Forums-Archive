---
title: "Boot time crash with ATI Radeon 3870 X2 is installed in PC"
date: 2009-05-11
forum: General Help
---

### Post by belong on 2009-05-11
I was trying to install Ubuntu Desktop on my home machine (after several successful installs in other locations). The first problem I encountered was that the Live CD would not boot - it would simply freeze just after attempting to detect hardware and load drivers.

I went about removing various bits of hardware (starting with the USB devices) and ended up at the point where I had removed the graphics card and was using the on board intel chipset. Finally, the live CD would boot and I went about installing ubuntu (kind of expecting there to be a problem when I put the graphics card back in, but went along with it anyway).

Installation was fine - had a little bit of work to do with ndiswrapper to get my wireless network card working but other than that all was well.

So I put the graphics card back in, crossed my fingers and rebooted. And it crashed while booting from the installation, at the same place (hardware detection, right at the start of the boot process)

In recovery mode the same thing happens though I do get a stack trace (at least, the last 24 lines of one) which I could photograph and post on here if that would be of any use - obviously as I cannot boot the live cd or the actual installation normally or in recovery mode, it's impossible to actually post anything from dmesg!

Hoping someone may be able to help. I am a fairly experienced linux user however when it comes to problems this early on in the boot process it's pretty much beyond my area of expertees!

Thanks,

Ben Longden.

---

### Post by pro003 on 2009-05-11
> **belong said:**
> I was trying to install Ubuntu Desktop on my home machine (after several successful installs in other locations). The first problem I encountered was that the Live CD would not boot - it would simply freeze just after attempting to detect hardware and load drivers.

I went about removing various bits of hardware (starting with the USB devices) and ended up at the point where I had removed the graphics card and was using the on board intel chipset. Finally, the live CD would boot and I went about installing ubuntu (kind of expecting there to be a problem when I put the graphics card back in, but went along with it anyway).

Installation was fine - had a little bit of work to do with ndiswrapper to get my wireless network card working but other than that all was well.

So I put the graphics card back in, crossed my fingers and rebooted. And it crashed while booting from the installation, at the same place (hardware detection, right at the start of the boot process)

In recovery mode the same thing happens though I do get a stack trace (at least, the last 24 lines of one) which I could photograph and post on here if that would be of any use - obviously as I cannot boot the live cd or the actual installation normally or in recovery mode, it's impossible to actually post anything from dmesg!

Hoping someone may be able to help. I am a fairly experienced linux user however when it comes to problems this early on in the boot process it's pretty much beyond my area of expertees!

Thanks,

Ben Longden.


Hi Ben. I had similar problems with couple of ATI's cards and that was always when I used Live CD for installation. Howerer, since then I found out that the Alternate CD which you can download is not causing such problems. Maybe you should give a try. If you look out for graphic problems across the forum you will find out that ATI's video cards are pretty major problem when it comes to Linux.

---

### Post by belong on 2009-05-12
Doing some messing around last night to further diagnose the problem, I replaced the ATI card with an old nVidia 6 series card, thinking that at least I could be up and running.

Same problem, same crash! It seems as if ANY PCIe card in the slot is causing a problem in initialising hardware!

The motherboard is an Intel 945G... I wonder if that could be the problem?

:confused:

---

### Post by mindry on 2009-05-12
This sounds the same as the problem I am having here [http://ubuntuforums.org/showthread.php?t=1154943](http://ubuntuforums.org/showthread.php?t=1154943) - again, using a graphics card which is known to work in another PC does not solve the problem. There must be someone who knows how to fix this as it's a complete showstopper on a relatively new machine.

---

### Post by pro003 on 2009-05-12
> **belong said:**
> Doing some messing around last night to further diagnose the problem, I replaced the ATI card with an old nVidia 6 series card, thinking that at least I could be up and running.

Same problem, same crash! It seems as if ANY PCIe card in the slot is causing a problem in initialising hardware!

The motherboard is an Intel 945G... I wonder if that could be the problem?

:confused:

and what about windows (if you have one installed? 
did same happens?

---

### Post by belong on 2009-05-16
Windows Vista is installed and working with no problems.

I actually gave up on Ubuntu and decided to try installing debian lenny - same problem.

Currently downloading the openSuse livecd as a test to see if that boots. At this point, I just need a working linux system! :-)

---

### Post by belong on 2009-05-16
OpenSuse fails to boot.

pcieport-driver reports an invalid IRQ - but a little research shows that this is a bug in the driver (as pcie doesn't use an interupt request).

The stack trace is more visibile here as it uses a larger console buffer - the crash seems to happen inside kmap_atomic_prot+0x76

Going to try booting ubuntu again to see if the two look to be crashing for the same reason...

---

### Post by mindry on 2009-05-16
That's odd, openSUSE works fine on my machine (I too have given up on ubuntu and variants as nobody has replied to my thread) so maybe I have a different problem with very similar symptoms. However installing the proprietary fglrx driver on openSUSE broke everything and it had to be removed from the command line so I wouldn't recommend that if you do get SUSE working. The impression I get is that ubuntu is just too buggy for some machines, but nobody seems interested.

---

### Post by pro003 on 2009-05-16
> **belong said:**
> Windows Vista is installed and working with no problems.

I actually gave up on Ubuntu and decided to try installing debian lenny - same problem.

Currently downloading the openSuse livecd as a test to see if that boots. At this point, I just need a working linux system! :-)

And please, answer: Did you try to install ubuntu with alternate i386 CD?

---

