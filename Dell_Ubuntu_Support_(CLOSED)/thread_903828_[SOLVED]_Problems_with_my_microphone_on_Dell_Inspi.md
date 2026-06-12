---
title: "[SOLVED] Problems with my microphone on Dell Inspiron 1525"
date: 2008-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by roland0702 on 2008-08-28
I'm trying to get my microphone to work so I can make calls on Skype. The sound recorded on the mic is played back to me extremely quiet. I have no idea what I am doing so any help is much appreciated.

Also, I purchased my laptop with Ubuntu 8.04 claiming it has DVD playback. I have not been able to play my DVDs. I do have the Ubuntu installation disc that came with my computer...

Kevin

---

### Post by ms_whosit on 2008-08-29
I have Gutsy so this is just a guess, but maybe try playing with the recording settings in volume-control? See here for example:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low)
or here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work)


You'll want to adjust either capture, digital, or mux--maybe all three. (I had to play around to figure out if I was using the digital or analog mic..turned out to be the digital one (couldn't get the analog one to work).)

For DVD playback--my 1525n/Gutsy came with a program called LinDVD. I would assume yours is supposed to have it as well, if not, maybe get on the phone with Dell..

---

### Post by Crafty Kisses on 2008-08-30
Post the results of > lspci

---

### Post by hob on 2008-09-02
I have an Inspiron 1420N laptop and have this exact same problem. I'm also trying to use an analog external mic hooked up to the Microphone jack for Skype. This laptop came from Dell with 7.04, and I wiped the / partition when upgrading with the standard DVD installer. I still have the same /home partition as 7.04, which may be causing some problems?

The internal microphone does work, but the audio is way too low (with all the inputs turned up) to be of any use; and I would like to use this very sensitive external mic anyways.

In the Options tab in gnome-volume-control, I set the "Digital Input Source" to Analog Inputs, and the three "Input Source" options to Mic. It seems this help is for 7.10, and I am running 8.04.

Here is the output of lspci for Codename:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


This is extremely frustrating, as it seems like the "upgrade" from 7.04 (I skipped 7.10) to the latest version was actually a downgrade: no input sound anymore, mouse/keyboard on the fritz after several hours, system grinds to a halt after about 6 hours, firefox crashes all the time after spawning extraneous small windows, desktop sftp folders not persistent across reboots....

Thanks for your help.

---

### Post by american.swan on 2008-09-02
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
03:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I am going to try and follow the direction on [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work) and see if they work for me.  I'll be back.

I don't have a Dell PC, but I'll see if it works anyways.

---

### Post by american.swan on 2008-09-02
Fixed it.  Had to go to volume control and in preferences get the right stuff open and unmuted.  

Mic works now.

---

### Post by hob on 2008-09-03
Hey american.swan, did you get the internal mic working or the microphone jack working? I don't care much about the internal mic, only the microphone jack to plug in an external microphone.

Also, do you remember which options you checked in gnome-volume-control? My options: Master, Headphones as Line Out, PCM, Front, Surround, Center, LFE, IEC958, Capture, Capture 1, Capture 2, Analog Loopback, Digital, Digital Input Source, Input Source, Input Source, Input Source, Mux, Mux 1, Mux 2, Swap Center/LFE.

What kind of computer do you have? Thanks.

---

### Post by american.swan on 2008-09-03
> **hob said:**
> Hey american.swan, did you get the internal mic working or the microphone jack working? I don't care much about the internal mic, only the microphone jack to plug in an external microphone.

Also, do you remember which options you checked in gnome-volume-control? My options: Master, Headphones as Line Out, PCM, Front, Surround, Center, LFE, IEC958, Capture, Capture 1, Capture 2, Analog Loopback, Digital, Digital Input Source, Input Source, Input Source, Input Source, Mux, Mux 1, Mux 2, Swap Center/LFE.

What kind of computer do you have? Thanks.

I don't exactly remember which options.  I checked the ones that seemed useful and might be related to the mic.  I got the mic jack working.  I am on a Samsung MV40

---

### Post by lwb4007d on 2008-09-04
[font=Times New Roman]**Very good!!!!**[/font]------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU2563439.jpg[/img]Well come to our site:buy [Warhammer Online Gold](http://www.toppowerlevel.net/gamelist.php?fid=3966) [2 Moons Dil](http://www.toppowerlevel.net/gamelist.php?fid=4048)  buy [RS Gold](http://www.toppowerlevel.net/gamelist.php?fid=4011) [SRO Gold](http://www.toppowerlevel.net/gamelist.php?fid=4013) [EVE Online ISK](http://www.toppowerlevel.net/gamelist.php?fid=4044)

---

### Post by gustavofuhr on 2009-01-05
Hi all ... I have working fine the external mic jack ...

I ve a Dell Insipiron 1525 with 
> 
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


I ve installed Ubuntu 8.10 about a week ago, and I was dealing with the mic jack problem ... there are forums threads that propose the alsa-base options 3stack, 5stack, 3stack-dell and auto .. but none of these works for me ... 
Later, I also removed/purged pulseaudio, and i dont known if this step is part of the solution.

finally I found:

options snd-hda-intel model=dell-bios

I placed it in alsa-base, rebooted the system .. and works!

I noticed too, that the two sound jacks from the front works together. Early, worked only one at time


In input source from kmix, now i have only two options, mic and front mic ... and with capture and mux sliders i control the recording level. The only issue with this, is that if I activate "Analog Loopback" the feedback plays very low. I known that it is working because I made a skype test call and sounds ok.

---

### Post by dmk99 on 2009-01-10
I have a Dell inspiron 1525 running Ubuntu 8.10. I was having problems with my headphone jacks not working together (only one would work at a time) until I found this thread. Adding "options snd-hda-intel model=dell-bios" to the end of /etc/modprobe.d/alsa-base and rebooting fixed the problem for me. Thank you!!

---

### Post by ItalOz on 2009-01-14
I've solved the problem by following the indications in
[http://ubuntuforums.org/showpost.php?p=4197874&postcount=13](http://ubuntuforums.org/showpost.php?p=4197874&postcount=13)

It worked on my DELL inspiron 1525 with Ubuntu 8.04

I just needed to slide up the controls of digital capture which did not appeared before.

---

