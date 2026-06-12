---
title: "Help, no sound"
date: 2009-03-05
forum: General Help
---

### Post by Saltwaterfishin on 2009-03-05
Hi all,

My brother gave me his old computer with UBUNTU on it.  So far I'm doing okay learning how to use it.  The problem I'm having is that I have NO sound at all.  The sound card in the computer is: Creative Labs SB 0090.  It also had Audigy SB 1394 on it.  I'm not sure if I'm having a driver problem or what to do.  I did find the MASTER sound and have it set at 100%.  Device in Master is showing Audigy 1 [SB0090](Alsa mixer).   Switches is showing Audigy Analog/Digital output jack.  I have the speakers plugged into "Digital Out" jack on the card. I've tried playing a music CD and also streaming audio from the net.  If anyone can help, please email me at [email]Saltwaterfishin@aol.com[/email].  The computer also turns itself ON daily. 

Much thanks in advance,

Jay

---

### Post by Nano_ext3 on 2009-03-05
What is the output of "lspci | grep audio"?  Please post that here.  Also you may want to go to your settings and to the "Sound" manager in Ubuntu.  The ALSA driver is known to work on many occasions where the real driver fails to work.  This happened to me on my desktop, which is understandable as it is choc full of custom hardware.  Change each entry on the main page of the sound editor to ALSA.  You can test the output by hitting the test button.  Change your driver if ALSA does not work, one of the drivers in each drop down should work, but you want to keep the same driver for all if you can.  

Hope this helps.

Cheers

--Nano

---

### Post by Saltwaterfishin on 2009-03-07
Hey Michael,

Thanks for the advice.  I guess I'm not as up on Ubuntu as I could be.  I'm not sure what lspci/grep audio is or where to find it.  I did a search and did find lspci but don't know how to access it.  I also found some help on this forum.  I don't think that the correct driver even exists on this computer.  I think I need one called emu10k2 which I did not find on the computer.  I did find emu1ok1 though and tried using that one...to no avail.  I also tried going to the Creative Labs web site and downloaded the "real" driver, but don't know how to install it.  Heck, I can't even get most of my executable files to work.  Up until a couple days ago I had only used MS windows.  This is all new to me.

Thanks again,

Jay

---

### Post by DeMus on 2009-03-07
> **Saltwaterfishin said:**
> Hey Michael,

Thanks for the advice.  I guess I'm not as up on Ubuntu as I could be.  I'm not sure what lspci/grep audio is or where to find it.  I did a search and did find lspci but don't know how to access it.  I also found some help on this forum.  I don't think that the correct driver even exists on this computer.  I think I need one called emu10k2 which I did not find on the computer.  I did find emu1ok1 though and tried using that one...to no avail.  I also tried going to the Creative Labs web site and downloaded the "real" driver, but don't know how to install it.  Heck, I can't even get most of my executable files to work.  Up until a couple days ago I had only used MS windows.  This is all new to me.

Thanks again,

Jay


To use the lspci command you have to do the following:
Click on menu Applications, top left of your screen
Choose Accessories
Choose Terminal

In the window which appears now, you type lspci and enter.
Select the output with the mouse and use "ctrl-shift c" to copy it. Then paste it (ctrl-v) into your answer here.
It should look something like this:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


I am wondering though about your line:
"I have the speakers plugged into "Digital Out" jack on the card."
Did you try using the analog output connector, mostly with a green color. Loudspeakers normally don't use digital sound.

Success.

---

### Post by Nano_ext3 on 2009-03-07
Yes, in "termainal" type "lspci | grep audio"

Still, in your Sounds , application under system settings , or prefrences (I cant remember im on Xubuntu right now) that menu should let you change the "driver" with a drop down list.  Start with the first one and keep trying a "driver" from the list and each time hitting test to see if a beep comes through your speakers.  

See this picture to know what menu I am referring to:

[http://img155.imageshack.us/img155/8377/screenshotsoundpreferenyv4.png](http://img155.imageshack.us/img155/8377/screenshotsoundpreferenyv4.png)

You probably want the "ALSA" entry under each entry, like I said hit the "test" button to confirm its working.

Cheers,

Nano

---

### Post by Saltwaterfishin on 2009-03-07
Hi all,

Thanks a bunch for all the advice.  Still no sound.  Here is the results from lspci.  BTW, when I have made any changes to any settings, I've tried to plug the speakers in to EACH jack that is available on the sound card to see if ANY sound comes through.



00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)

---

### Post by Saltwaterfishin on 2009-03-07
Here is the result of lspci | grep audio

jay@jay-desktop:~$ lspci | grep audio
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


Thanks again,

Jay

---

### Post by MIJ-VI on 2010-03-29
Aaannnd over a year later...

Have you tried running alsamixer in Terminal and un-muting all of the audio card's inputs & outputs and increasing the gain of each one via the up & down arrow keys on the keyboard?

---

