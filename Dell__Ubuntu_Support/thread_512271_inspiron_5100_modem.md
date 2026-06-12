---
title: "inspiron 5100 modem"
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by fenario on 2007-07-29
Fenario, Australia, Dell Inspiron 5100
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_19
ALSAversion 1.0.13
USB modem not detected by lsusb

Hi Friends

I have done the in between step of weaning myself of the bloated giant and, as well as XP, installed ubuntu. ( Thanks to all you admirable brains. Take of all my hats to you all) om my  laptop.
It has a softmodem as well as PCMCIA card modem. So far I haven not gotten it to work.

_PCMCIA PC card modem _on COM 4:

PCMCIA/PRETEC-compact modem_3.3V_56k-8DEC
type CVFM-5614
on Texas Instruments PCI-4510 Card Bus Controller:
VID: 104C
DID: AC44
subVID: FE00 rev.: 02
This modem works better on my 3hop radio phone.

The other is a _softmodem PCTel 2304WT V.9x MDC Modem _on COM 3

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	134d:4c21	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  7:        610    XT-PIC-XT        eth0, Intel 82801DB-ICH4

 --- Bootup diagnositcs for card in PCI slot 00:1f.6 ----
[   27.178064] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   27.178074] ACPI: PCI interrupt for device 0000:00:1f.6 disabled


Another complication may be this:
I have a prepaid phone account which requires me not to wait for the dialtone! 
I believe this need to be written into the modem config (X3) 
under windows this would be:
uncheck > wait for dial tone before dialling 
-where abouts does the line go?
-any prefix?

A voice announces prompts then the number gets dialled, all at once 
So It needs a pause at first (under windows it's done via five  ,,,,,)
then this very long number that includes account nr , pin and phonenumber of ISP followed by #.

Has anyone managed to get either of the two modems working?
I'd appreciate some help as i'm a novice and feeling a bit inadequate.

Thanks and regards
Fenario
:guitar:
PS
 I just got kernel linux-2.6.21.1.tar.bz2
Would this be more useful as I read somewhere that the next kernel
may have softmodem support?

---

### Post by Paul S on 2007-07-30
linmodems.org mailing list can probably answer better.

regards,

---

### Post by fenario on 2007-08-01
Thanks to all concerned

I can't believe how much trouble and questions people have with ubuntu.
I thought I had a good thing, just install it and drive it.
Well far from that. All I can do is look at jpgs and play solitaire.
mp3s,  mpgs and other files won't work. Is that all?
What can I actually expect?

Windows works fine, so why change to another system?
I want to have proper argument, but not " i hate microsoft"; that is a weak argument. I know windows is clumsy and heavily controlled by MS.

So what is the real advantage of ubuntu and will it ever become an OS that works from the start?

Getting tired of too many long nights trying to get this going and running down my precious solar power.
fenario

---

