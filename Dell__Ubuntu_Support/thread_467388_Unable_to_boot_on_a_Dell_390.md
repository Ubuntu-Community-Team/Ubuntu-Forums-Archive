---
title: "Unable to boot on a Dell 390"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by jeff7360 on 2007-06-07
I want to load Feisty on my Dell 390, but I can't get the LiveCD to boot on the system. It gives me an error stating: "Can't access TTY". I removed the quiet and splash boot options. When the system starts the boot process it seems to run fine until the fd0 is mounted. It says that the port did not respond, or is slow. Then after a few times of attempting to mount fd0 it gives me the TTY error. 

Any ideas how to resolve this?  (still a little green when it comes to linux)

---

### Post by Ek0nomik on 2007-06-07
Have you by any chance looked at this thread?

[http://ubuntuforums.org/showthread.php?t=279884](http://ubuntuforums.org/showthread.php?t=279884)

---

### Post by jeff7360 on 2007-07-09
I checked that other thread. They where all having issues with booting AFTER having installed Ubuntu. I can't get the LiveCD to boot. It gets stuck while trying to access the floppy drive. I guess to mount it? Then it gives me the TTY error.

---

### Post by lbrspec on 2007-07-18
> **jeff7360 said:**
> I checked that other thread. They where all having issues with booting AFTER having installed Ubuntu. I can't get the LiveCD to boot. It gets stuck while trying to access the floppy drive. I guess to mount it? Then it gives me the TTY error.



i'm haveing the same issues w/ my dell 390

---

### Post by lbrspec on 2007-07-18
i should be a bit more specific.  I'm a bit of a noob so please bear w/ me.

after post it picks up on the cd goes to the cd's boot loader and asks stuff, i pick start/install.  the little ubuntu logo comes up w/ the scrolling bar under it.  after 20 sec.s or so i get the fallowing errors

/vin/sh: can't access tty; job control turned off
(initramfs) [44.568321] ata5; port failed to respond (30 secs, Status 0xd0)

then there are a few more lines of garble upon request i will enter them, but it finally ends w/ a (initramfs) prompt. :confused: I've updated to the latest dell bios 2.0.3 but that didn't help either.

thanks in advance,
matt

---

### Post by strabes on 2007-07-18
Have you tried the alternate CD?

---

### Post by lbrspec on 2007-07-18
i have tried two different disks and downloaded it twice from the ubuntu site it is version 7.04.  I was thinking too my first disk was bad, i burnt a second one and it did the same so i thought there might be something corupt in the download so i downloaded it again and cut another disk.  same bit.  Do you think that there may be a 7.03 that may work better or a different iso?  I"m open to suggestions.

thanks again
matt:)

---

### Post by earth on 2007-07-18
My Dell Dimension 4600C will boot and run several Linux Live CDs, but not Ubuntu 7.04.  I'm not interested in learning the command line or hassling with fixing this problem, but report this technical information for Ubuntu, so that I may run their next Live CD in this machine.  Here's the technical information:

Detected Hardware -- Dell Dimension 4600C

Successfully Boots & Runs the following Live Linux CDs: Knoppix 5.0, Puppy 2.10r1, and PC Linux 2007 (Installed on Hard Drive).

Unsuccessful in booting Ubuntu 7.04 & Fedora 7.  Ubuntu freezes at "Loading"; Fedora 7 freezes on desktop page.

Here are the specifications from the PCLinuxOS Control Center for Detected Hardware

1.  Identification
Vendor: &#8206;Western Digital Corp.

Model: &#8206;WD800BB-75CAA0

Media class: &#8206;hd


2.  Identification
Disk identifier: &#8206;QSI CD-RW/DVD-ROM SBW-242

Media class: &#8206;cdrom


3.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82865G [Springdale-G] Chipset Host Bridge

Media class: &#8206;BRIDGE_HOST


4. Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;865 Chipset Graphics Controller

Media class: &#8206;DISPLAY_VGA


5.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB AC'97 Audio

Media class: &#8206;MULTIMEDIA_AUDIO


6.  Identification
Processor ID: &#8206;1

Vendor: &#8206;GenuineIntel

Model name: &#8206;Intel(R) Pentium(R) 4 CPU 2.40GHz

Cpuid family: &#8206;15

Model: &#8206;2

Model stepping: &#8206;9


7.  Identification
Vendor: &#8206;Broadcom Corp.

Description: &#8206;BCM4401 100Base-T

Media class: &#8206;NETWORK_ETHERNET

8.  Connection
Vendor ID: &#8206;0x0000

Device ID: &#8206;0x0000

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Misc
Name: &#8206;Not Specified

Installed size: &#8206;8 KB

Type: &#8206;Cache

Connection
Vendor ID: &#8206;0x0000

Device ID: &#8206;0x0000

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Misc
Name: &#8206;Not Specified

Installed size: &#8206;512 KB

Type: &#8206;Cache


9.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB ICH5 IDE

Media class: &#8206;STORAGE_IDE

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;31

PCI function #: &#8206;1

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24db

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;ata_piix


Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB ICH5 IDE (SATA)

Media class: &#8206;STORAGE_IDE

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;31

PCI function #: &#8206;2

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d1

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;ata_piix

10.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;USB Controller

Media class: &#8206;SERIAL_USB

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;29

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d2

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;uhci-hcd


Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;USB Controller

Media class: &#8206;SERIAL_USB

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;29

PCI function #: &#8206;1

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d4

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;uhci-hcd

Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;USB Controller

Media class: &#8206;SERIAL_USB

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;29

PCI function #: &#8206;2

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d7

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;uhci-hcd


Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB USB EHCI Controller #2

Media class: &#8206;SERIAL_USB

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;29

PCI function #: &#8206;3

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24de

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;uhci-hcd


Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;USB Enhanced Controller

Media class: &#8206;SERIAL_USB

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;29

PCI function #: &#8206;7

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24dd

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;ehci-hcd


11.  Identification
Vendor: &#8206;Linux 2.6.18.8.tex5 ehci_hcd

Description: &#8206;EHCI Host Controller

Media class: &#8206;Hub|Unused

Connection
Bus: &#8206;USB

Bus PCI #: &#8206;5

PCI device #: &#8206;1

Vendor ID: &#8206;0x0000

Device ID: &#8206;0x0000

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Misc
Module: &#8206;hub


Identification
Vendor: &#8206;Linux 2.6.18.8.tex5 uhci_hcd

Description: &#8206;UHCI Host Controller

Media class: &#8206;Hub|Unused

Connection
Bus: &#8206;USB

Bus PCI #: &#8206;4

PCI device #: &#8206;1

Vendor ID: &#8206;0x0000

Device ID: &#8206;0x0000

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Misc
Module: &#8206;hub


12.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB SMBus

Media class: &#8206;SERIAL_SMBUS

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;31

PCI function #: &#8206;3

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d3

Sub vendor ID: &#8206;0x1028

Sub device ID: &#8206;0x0154

Misc
Module: &#8206;i2c-i801


13.  Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82820 815e (Camino 2) Chipset PCI

Media class: &#8206;BRIDGE_PCI

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;30

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x244e

Sub vendor ID: &#8206;0xffff

Sub device ID: &#8206;0xffff

Misc
Module: &#8206;hw_random


Identification
Vendor: &#8206;Intel Corp.

Description: &#8206;82801EB ISA Bridge (LPC)

Media class: &#8206;BRIDGE_ISA

Connection
Bus: &#8206;PCI

Bus PCI #: &#8206;0

PCI device #: &#8206;31

PCI function #: &#8206;0

Vendor ID: &#8206;0x8086

Device ID: &#8206;0x24d0

Sub vendor ID: &#8206;0xffff

Sub device ID: &#8206;0xffff

Misc
Module: &#8206;i8xx_tco


14.  Identification
Vendor: &#8206;

Description: &#8206;AT Translated Set 2 keyboard

Connection
Bus: &#8206;isa

Vendor ID: &#8206;0x0001

Device ID: &#8206;0x0001

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Misc
Module: &#8206;kbd


15.  Identification
Name: &#8206;Optical Mouse

Connection
Bus: &#8206;USB

Bus PCI #: &#8206;3

PCI device #: &#8206;3

Vendor ID: &#8206;0x046d

Device ID: &#8206;0xc016

Sub vendor ID: &#8206;0x0000

Sub device ID: &#8206;0x0000

Features
Emulated wheel: &#8206;No

Misc
Vendor: &#8206;Logitech, Inc.

Media class: &#8206;Human Interface Devices|Boot Interface Subclass|Mouse

Description: &#8206;Optical Mouse

Module: &#8206;hidups

---

### Post by lbrspec on 2007-07-20
i was able to get a 6.06 to work, but i'd like the new features in 7.  Does anybody have any idea what is causing this and if there is a quick fix or a different subversion that would work better?

thanks again,
matt

---

### Post by jeff7360 on 2007-07-20
strabes,

       I have yet to try the Alt CD. I will check it out to see if this will resolve the issue.

---

### Post by cdale on 2007-08-14
I too was unsuccessfull in ibooting from the 7.04 live CD on my Dell Percission 390. I recieved the same errror message.  

However I found that I was able to successfully install the 6.06 LTS, then do the online update to 7.04  

It is kind of the long way round to get there, but the end result is the same.

Cheers. :popcorn:

---

### Post by jeff7360 on 2007-10-17
So, I finaly got around to downloading and trying the Alt CD. Same thing happens as with the LiveCD only this time the text based installer loads. As I move through the installer I notice nothing unusual, until the hardware detection. It begins to detect that hardware in the machine so it can mount the CDrom. it cannot mount the cd drive. Which is the issue with booting the live cd, the cdrom cannot be mounted. It reports that ATA5 is slow to respond, ATA5 responded abnormally, then it bombs out.

Does anyone know how i can resolve this?

---

