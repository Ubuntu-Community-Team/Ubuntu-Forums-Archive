---
title: "[SOLVED] Install Ubuntu 7.10 on Dell L700cx"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinGNUbie on 2008-05-06
I have a Dell L700cx that I want to try Ubuntu 7.10 out on. It has a Celeron 700MHz, BIOS AO9, 128Mb RAM (512Mb on the way), Unknown Video, 40Gb primary hdd, 4Gb secondary hdd, (both SCSI (/dev/sda & /dev/sdb) according to GParted), NO OS's or even DOS on the drives.

I don't have anything but the Ubuntu 7.10 LiveCD (from Linux Store, CA), a created GParted LiveCD from .iso image, and *yawn* dial-up access @ less than 56k on another PC (Win98 4.10.2222 which I hope to network to the Ubuntu) at my disposal.

I have tried for about 4 days and every which way I can find in the forums to install it (including using Partition Magic, Gparted LiveCD, Win98 CD to partition hdd's, unformatted, formatted as ext3, w/ & w/o: options-ubiquity, acpi=force irqpoll, all to no avail.

It seems that each time I try to install, sometimes finishing, after reboot, nothing on the drives, no bootable partitions, or just sits there and blinks the cursor, taunting me, lol. The ONLY constants through these proceedings I have noticed are the [failed to reset NO_REBOOT flag] (every time), 156: CPU frequency scaling not supported, when I use the GParted LiveCD I have to use Forcevideo and use "dummy" or "vesa", and that I drink a lot of tea.

I fail to believe that Linux can be this hard to install on a PC, and am wanting to make the move into new OS's other than Windows. (Loooooong time Win98 user, I prefer it's flexibility to newer versions.)

Does anyone have insight or ideas as to getting it onto this pc?

---

### Post by twright on 2008-05-06
by the sound of it your PC isn't fast enough to run Ubuntu, if you try Damn Small Linux (only 50 meg, it will still take a while but better than 700 at least) that should work fine

---

### Post by LinGNUbie on 2008-05-06
According to Ubuntu's recommended requirements, I am within parameters (except for the memory @ the moment) to run at full speed, but plenty enough to install. Thanks for the steer towards DSL, I was wanting to investigate it further, too. Might just have to sooner than I thought.

---

### Post by LinGNUbie on 2008-05-14
*UPDATE*
I managed to get it installed with the original 128Mb of memory (still waiting for the 512Mb upgrade to arrive), however I am not quite sure what the problem was. Since for some reason the partitions weren't taking, I decided to install a minimal Win98 to see if it would take, It did. After verifying that the devices were all functional on this system, and able to connect to the internet with dial up & connect to other machines using the LAN I again moved to partitioning with GParted, which now took! After rebooting with the Ubuntu 7.10 LiveCD, lo and behold, success! Installed and operational on hdd, although the network and dial up access are not yet functional.

Any advice would still be appreciated!

---

### Post by LinGNUbie on 2008-05-19
After managing somehow to get it at least installed and bootable on the dell, I got the new RAM installed and thought I might try a new  fresh install with ubuntu as the only OS. After reformatting and partitioning the drives (using GParted) I decided to give it a go.

No success w/ Desktop CD. Either fails to (initramfs) or fails to load X. - Turns out I had two problems, a failing cdrw & I had received a bad CD, so waiting on alternate CD to arrive/download to reattempt.

I have noticed that there seems to be a configuration issue with the Intel 810 chipset being configured by the installers on the GParted and Ubuntu CDs, neither X loads, and Forcevideo script will not run correctly on Gparted leaving me to run fdisk, cfdisk, or parted manually from command line each time.

Any insights?

---

### Post by LinGNUbie on 2008-06-10
-UPDATE *by a new linux user*,

After receiving new CD's from CheapBytes, and discovering a gently used Gateway PC with a three ide interface, I abandoned the Dell for another time. Installation was successful with 7.10 on the Gateway, although I am still trying to configure the transfered Winmodem to connect via dial-up because the Gateway Telepath was not recognized. 1 more year for DSl Verizon says! Networking without a hiccup to the windows machines locally via ethernet **without** samba installed, curiously.

- UPDATE (2)

Once the issues with a bogus CD and the failing drive were straightened out, I re-attempted the Dell installation with complete success! Once installed, I moved to compiling and installation of the martian_modem driver for the Lucent/Agere winmodem as per the instructions posted here on the forum ([http://ubuntuforums.org/showthread.php?t=328050]("http://ubuntuforums.org/showthread.php?t=328050")), also with success! BTW, no restricted or special drivers were required for any other hardware for the pc, besides the winmodem. If anyone else is having related issues with installations, I recommend ensuring that the CD/DVD is not corrupted in some manner and that all hardware on the machine is in good working order, as it seems that this was the primary reason for my issues with installation.

---

