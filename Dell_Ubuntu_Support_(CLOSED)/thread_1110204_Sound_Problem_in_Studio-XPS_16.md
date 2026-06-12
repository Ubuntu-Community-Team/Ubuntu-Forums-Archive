---
title: "Sound Problem in Studio-XPS 16"
date: 2009-03-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vish999 on 2009-03-29
I recently changed to ubuntu 8.10 and am new to linux :( 
my laptop has two sound jacks
the laptop front speakers also play the sound when headphones is plugged in the first jack.
but when plugged in the second both headphone and speaker do not respond.
what should i do to make sound play only in the headphones when plugged in? 
:confused:

---

### Post by aniketvb on 2009-03-30
Please post output of "lspci -nn"

---

### Post by Vish999 on 2009-03-31
here's it 

user@BlueMonster:~$ lspci -nm
00:00.0 "0600" "8086" "2a40" -r07 "1028" "0272"
00:01.0 "0604" "8086" "2a41" -r07 "" ""
00:1a.0 "0c03" "8086" "2937" -r03 "1028" "0272"
00:1a.1 "0c03" "8086" "2938" -r03 "1028" "0272"
00:1a.2 "0c03" "8086" "2939" -r03 "1028" "0272"
00:1a.7 "0c03" "8086" "293c" -r03 -p20 "1028" "0272"
00:1b.0 "0403" "8086" "293e" -r03 "1028" "0272"
00:1c.0 "0604" "8086" "2940" -r03 "" ""
00:1c.1 "0604" "8086" "2942" -r03 "" ""
00:1c.3 "0604" "8086" "2946" -r03 "" ""
00:1c.5 "0604" "8086" "294a" -r03 "" ""
00:1d.0 "0c03" "8086" "2934" -r03 "1028" "0272"
00:1d.1 "0c03" "8086" "2935" -r03 "1028" "0272"
00:1d.2 "0c03" "8086" "2936" -r03 "1028" "0272"
00:1d.7 "0c03" "8086" "293a" -r03 -p20 "1028" "0272"
00:1e.0 "0604" "8086" "2448" -r93 -p01 "" ""
00:1f.0 "0601" "8086" "2919" -r03 "1028" "0272"
00:1f.2 "0101" "8086" "2928" -r03 -p8f "1028" "0272"
00:1f.3 "0c05" "8086" "2930" -r03 "1028" "0272"
00:1f.5 "0101" "8086" "292d" -r03 -p85 "1028" "0272"
01:00.0 "0300" "1002" "9593" "1028" "0272"
01:00.1 "0403" "1002" "aa20" "1028" "0272"
04:00.0 "0280" "8086" "4232" "8086" "1321"
08:00.0 "0200" "14e4" "1698" -r10 "1028" "0272"
09:01.0 "0c00" "1180" "0832" -r05 -p10 "1028" "0272"
09:01.1 "0805" "1180" "0822" -r22 -p01 "1028" "0272"
09:01.2 "0880" "1180" "0843" -r12 "1028" "0272"
09:01.3 "0880" "1180" "0592" -r12 "1028" "0272"
09:01.4 "0880" "1180" "0852" -rff -pff "" ""

---

### Post by Vish999 on 2009-03-31
user@BlueMonster:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility HD 3670 [1002:9593]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
04:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

---

### Post by Cpudan80 on 2009-04-06
I'm having this same issue -- the old workarounds which mention tying line-in to output don't work as those options are ... gone.

Here's the output for lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility HD 3670 [1002:9593]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
04:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

---

### Post by tyl3r. on 2009-04-18
Same problem here with my XPS16

$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility HD 3670 [1002:9593]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

---

### Post by tyl3r. on 2009-04-18
ok I got one jack to work now....

add options snd-hda-intel model=ref

to /etc/modprobe.d/alsa-base

For me 1 Audio jack is working now. My XPS16 has 2 jacks on the left side, the inner one is working now, the first one not but thats ok for now...I can live with that until I find out how to get both to work ;)

**@Vish999**: I just saw your problem was actually different with front also playing while jack plugged in. Try the solution above, if not working, try booting ubuntu with the cable in the jack already plugged in...I remember that helped some time ago when I had that issue on another Notebook

---

### Post by tyl3r. on 2009-04-18
fyi, I currently use Intrepid 8.10 64Bit with alsa firmware/driver 1.0.17

Will try to update  to 1.0.19 tomorrrow using the script here....

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)


I will post the results then (if someone updates to 1.0.19 before, please let us know the result here)

regards,
tyl3r

---

### Post by likqidred on 2009-04-19
I seem to have this same problem,front jack works but speakers keep playing, rear jack nothing at all,will keep an eye on this thread.:)

---

### Post by Supa_Fly on 2009-04-22
I've had the same problem on my XPS with the new Jaunty release; it seems some tracks are set to mute, by default (I have no idea why this is).
Click on the speaker icon on your control panel.
Select HDA Intel (Alsa mixer) in the Device drop-down menu.
Click on "Preferences" & make sure that all the boxes are selected, right down to Analog Loopback. Close the Preferences window.
Now make sure that the Center & LFE controls are not muted.
This worked for me in getting both headphone jacks working, hope it works for some of you. ;-)

---

### Post by Jammanuser on 2009-04-22
For all those with the Dell Studio 1535, see [post=7116686]this post[/post].
Those are the steps I performed to get my earphones to work in Intrepid on the Studio 1535.

---

