---
title: "Wireless not working on Latitude D630"
date: 2012-08-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Masz52 on 2012-08-06
I'm new to Ubuntu and I'm trying out 12.04 on a Dell Latitude D360  laptop via USB flash drive. Everything seems to work except for  wireless. I'll download the drivers with an ethernet cable, and restart  the laptop, but then Ubuntu crashes when it's trying to start up.

I'm not sure what other info might be needed. I did try searching for solutions first but I think they were alternate ways to download the drivers and they didn't work. I'm not sure what else to do to solve this problem.

---

### Post by valley1967 on 2012-08-10
if you can can you give the output of lspci?

---

### Post by Masz52 on 2012-08-11
Thanks for the reply. I hope I did this correctly.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

Is there any chance me running this from a USB drive has anything to do with this problem? I didn't want to install this onto the hard drive until I got this issue sorted out.

---

### Post by wildmanne39 on 2012-08-11
Hi, for the driver you install to stay when you reboot you will have needed to make the usb stick persistent, but that is an easy card to get to work so I suggest you just install ubuntu.

You can do a clean boot into ubuntu on the flash drive then open a terminal ctrl+atl+t and copy and paste:
```
sudo apt-get install linux-firmware-nonfree
```
Then:
```
sudo modprobe b43
```
if you installed any other driver it will conflict with this one.
Thanks

---

### Post by Masz52 on 2012-08-13
I installed Ubuntu on the hard drive, and the wireless drivers were installed, and Ubuntu didn't crash when it rebooted, but wireless still doesn't work. The wi-fi switch was on, so I'm not sure what the problem is this time.

---

### Post by wildmanne39 on 2012-08-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Moose on 2012-08-13
I had the same problem with my HP G62. I think the problem might be from lack of drivers. Because if you are using an inbuilt wi-fi adapter the drivers will be pretty rare or even non existant. I found a good way to get around this problem was to take the password off of your wifi. ( I Only did this at nighttime to prevent peeps from stealing wifi) I took password off and for some strange reason it could work. If not you can also try pressing connect to hidden network and put your wifi details in there. That has worked aswell.
 
My ideas may or may not work because this problem has been different for most people who experienced it. If they do work, then Glad i could help! 
 
-Anarchy 
(Hooray first post!(I used to have account on here but forgot username and pass because i stopped using 'Buntu for a while))

---

### Post by Masz52 on 2012-08-14
> **wildmanne39 said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
ThanksOkay, here it is. I also want to say that since my last post, I enabled dual booting (Windows Vista + Ubuntu) and since then the wi-fi light has been on even while on Ubuntu. Though there still isn't any option for wireless.

---

### Post by wildmanne39 on 2012-08-14
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
it should work now if not run the info.text again and post here so we can see the change since running the commands above.
Thanks

---

### Post by Masz52 on 2012-08-14
That did it! Thank you very much for your help.

---

### Post by wildmanne39 on 2012-08-14
Your welcome!
Enjoy

---

### Post by RadioFreq on 2013-05-01
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
it should work now if not run the info.text again and post here so we can see the change since running the commands above.
Thanks


I know this is an old post, but helped me out today. Dell Latitude D630, fresh install of 12.04 LTS and had same problem. Followed your instructions and worked perfectly. Its good to be back in the Linux world!

RadioFreq

---

