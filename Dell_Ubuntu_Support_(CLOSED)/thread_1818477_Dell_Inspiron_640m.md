---
title: "Dell Inspiron 640m"
date: 2011-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JuDe Snow on 2011-08-04
Hello, 

**I am VERY new to Edubuntu**._ I read a lot of posts a little bit over the web to solve the little problems I have_, but they are very hard for me to understand. If you are able to help me please know that I installed Edubuntu yesterday on my computer and don't know where things are yet. 
Edubuntu is working GREAT!! ... but I have a few issues that I want to solve. I'll write them in order of importance. 
I installed Edubuntu erasing windows XP. Everything I am writing below worked fine under Microsoft.


[LIST=1]
[*]Internet works only when I am connected with a wire. It does not detect any wireless. How do I get that solved?
[*]My battery which use to last 5 hours with Windows goes out a lot faster even after I changed to power settings to help the computer. Is there a way to make the battery last longer?
[*]When using Skype, it detects I have a webcam, but it does not work. It also doesn't detect the microphone that is built-in the camera.
[/LIST]
I know it is a lot !! Thank you in advance for the help. :KS

---

### Post by mikewhatever on 2011-08-05
Hi and welcome to the forums,

1. Look for the Drivers utility under System->Administration. It's named either Additional Driver or Hardware Drivers. If there is a driver for your card in the Ubuntu repositories, the utility should help with installing it. If there is no driver, open Applications->Accessories->Terminal, type **lspci**, hit enter, and post the output which should show if the wireless card is detected.

2. Not sure there is something you can do. My guess is, you probably have Edubuntu 11.04 installed, which is affected by the high power consumption kernel bugs. Use the System Monitor from System->Admnistration to see if any of the processes consume a lot of CPU.

3. Knowing more about your computer and the camera might help, as well as the output of **lsusb** from the aforementioned Terminal.

---

### Post by JuDe Snow on 2011-08-05
Hi, thank you for the help.
 
 
1. Additional Drivers: Broadcom STA wireless drive (This driver is activated and currently in use.) I installed it when installing Edubuntu 11.04, but it still does detect any wireless connection.[INDENT]**lspci** results: 
 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01) 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller 
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
[/INDENT]2.  Doesn't really matter. Thanks for the info. :)

3. Camera: Microsoft LifeCam VX-1000
    Computer: What information would you need? 
[INDENT]**lsusb** results:
 
Bus 005 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



[/INDENT]

---

### Post by mikewhatever on 2011-08-06
The wireless issue needs some more troubleshooting. Can you post the output of the following:

```
lsmod | grep -e b43 -e wl
```

Try removing the STA wireless driver and installing b43 - a different driver that is reported to work with BCM4311. The packages to install after removing STA are **firmware-b43-installer b43-fwcutter**. The following command will do it all:
```
sudo apt-get purge bcmwl-kernel-source && sudo apt-get install firmware-b43-installer b43-fwcutter
```

Source:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038)

---

### Post by JuDe Snow on 2011-08-06
1. I removed the software. Here is the output I got for lsmod | grep -e b43 -e wl
                          wl                   2642531  0 
                          lib80211               14570  1 wl[INDENT]I installed the **firmware-b43-installer b43-fwcutter **packages( by putting the command you posted in the terminal, then disconnected the internet cable to see what it would do. It did not detect any wireless network. 

[/INDENT]3.

---

### Post by mikewhatever on 2011-08-07
I think a reboot is required in this particular case. If it still doesn't work, post the outputs of the following:
```
lsmod | grep -e b43 -e wl

ifconfig

rfkill list all
```

---

### Post by SeijiSensei on 2011-08-07
I avoided problems with the Broadcom card by having Dell install an Intel wireless card when we purchased our 640m.  It has worked perfectly for about five years now.  Replacing the wifi card yourself is a pretty simple task.  You open a door on the bottom of the machine and swap the devices.  

You can buy a [new Intel card from Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106040") for about $25.  It might be a better solution than spending hours of your time trying to get the Broadcom chip to work.

If you'd rather futz with the Broadcom, take a look at solutions that use [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  I recall seeing reports that worked with the Broadcom card.

---

### Post by JuDe Snow on 2011-08-07
> **mikewhatever said:**
> I think a reboot is required in this particular case. If it still doesn't work, post the outputs of the following:
```
lsmod | grep -e b43 -e wl
 
ifconfig
 
rfkill list all
```
 
 
1. Solved  Woohoo... it works. ( I forgot to reboot... silly me) :KS
2. I consider it as solved since not important. :KS
 
Thank you so much!!! yeeepeeee! :P
 
3. Is there anything I can do for the webcam?

---

### Post by mikewhatever on 2011-08-07
Can you elaborate on the webcam problems a bit. What do you mean by 'skype detects the webcam but it doesn't work'? What happens exactly. The microphone should appear as a new device in the Sound Preferences, Input Tab. Does it? What happens when you select it?

---

### Post by JuDe Snow on 2011-08-07
The webcam works fine under windows.


The microphone[INDENT]I went and configured the sound options. The computer detects the microphone and it detects sound. I did a sound test with the sound recorder and it works. Same thing with Skype so that's now all good.

[/INDENT]The video[INDENT]When I try to do a test it doesn't work (the screen stays black). The only webcam I can select under Skype is USB camera (dev   video0).


I tested the webcam with Empathy internet messaging and appart from being pink, it works fine both audio and video.

[/INDENT]

---

### Post by mikewhatever on 2011-08-07
Try the suggestion here -> [https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)
I have an old USB webcam that only works if an application is launched with LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so, for example:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by JuDe Snow on 2011-08-19
On skype the webcam doesn't work. Even after entering the code you mentioned.
The sound works fine:p, but the video does not start so it's half way there!! better than before!  I can't find anything that is helping in the trouble shooting link you sent :-(

---

