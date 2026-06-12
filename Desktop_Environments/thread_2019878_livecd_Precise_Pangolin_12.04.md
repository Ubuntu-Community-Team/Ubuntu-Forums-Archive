---
title: "livecd Precise Pangolin 12.04"
date: 2012-07-07
forum: Desktop Environments
---

### Post by lmart on 2012-07-07
Booted LiveCD on my laptop. No issues. Booted on my desktop. Issues. #1, when the try ubuntu page presented, the text was garbled. #2, could not connect with wireless even though all information was entered correctly.

What can I provide that will help you help me?
Thanks

---

### Post by msammels on 2012-07-07
When you say "try ubuntu page" what do you mean?

---

### Post by irv on 2012-07-07
> **lmart said:**
> Booted LiveCD on my laptop. No issues. Booted on my desktop. Issues. #1, when the try ubuntu page presented, the text was garbled. #2, could not connect with wireless even though all information was entered correctly.

What can I provide that will help you help me?
Thanks

You said when you booted LiveCD on your laptop, you had no issues. But the problems were with the desktop. I would have thought any wieless would have been associated with the laptop not the desktop. Don't you have a wired network with the desktop? Or do you have a wireless card in the desktop? It would be nice to have more information on your system you are having problems with. and that includes the video card also.

---

### Post by lmart on 2012-07-07
Thanks for your replies.

#1 When you boot the LiveCD, a page is presented that has 2 options; Try Unbuntu & Install Ubuntu.

#2 My laptop and desktop are both wireless. The LiveCD connected to the laptop wireless without a problem. No so with the desktop wireless. Triple checked all wireless parameters and they were correct. 

With that said, what do you need to know to help me connect the wireless on the desktop. Additionally, since the "try ubuntu" page comes up garbled every time on the desktop, my sense is there is something wrong, but I have no idea what it is or how to check any log that might give a clue.

---

### Post by irv on 2012-07-07
Could use a little more information on the desktop. What brand? Dell, IBM, etc? or is a home built one? What is the graphic card? Can you plug in a network cable? You may need to do this to try to get the wireless to work. It may need a driver. For some reason, the wireless card may not be supported or the driver for it is not loaded. You can check support for hardware at: [https://wiki.ubuntu.com/HardwareSupport/]("https://wiki.ubuntu.com/HardwareSupport/")
There is a link to wifi support on this page. Also video cards.

---

### Post by lmart on 2012-07-09
Hope this helps.

Devices

Processor
	Name	Intel(R) Celeron(R) CPU 2.60GHz
	Family, model, stepping	15, 2, 9 (Pentium 4)
	Vendor	Intel
Configuration
	Cache Size	128kb
	Frequency	2591.23MHz
	BogoMIPS	5182.46
	Byte Order	Little Endian
Features
	FDIV Bug	no
	HLT Bug	no
	F00F Bug	no
	Coma Bug	no
	Has FPU	yes

Memory
	Total Memory	2073772 kB

PCI Devices
	Host bridge	Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	VGA compatible controller	Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA controller])
	USB Controller	Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	USB Controller	Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	USB Controller	Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	USB Controller	Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	PCI bridge	Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	ISA bridge	Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	IDE interface	Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	SMBus	Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Multimedia audio controller	Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Ethernet controller	Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

USB Devices
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
	Microsoft® Nano Transceiver v2.0	
EHCI Host Controller
	Compact Wireless-G USB Adapter

Sensors
Input Devices
	Microsoft Microsoft® Nano Transceiver v2.0	
	Microsoft Microsoft® Nano Transceiver v2.0	
	Microsoft Microsoft® Nano Transceiver v2.0	
	Microsoft Microsoft® Nano Transceiver v2.0	
	Microsoft Microsoft® Nano Transceiver v2.0	
	Microsoft Microsoft® Nano Transceiver v2.0	
	Power Button	
	Power Button	
	PC Speaker

Storage
SCSI Disks
	ATA WDC AC25100L	
	HL-DT-ST CD-RW GCE-8483B	

DMI
BIOS
	Date	10/02/2003
	Vendor	Phoenix ([www.phoenix.com](www.phoenix.com))
	Version	6.00
Board
	Name	Imperial
	Vendor	TriGem Computer, Inc.

---

### Post by irv on 2012-07-09
Have you checked your hardware against the Hardware Supported list in the link above?
I see you have a network card so you may need to hook a wire up to it to get on line. I don't know if it is seeing your USB wireless. Also this is what it said about your video card.
[ATTACH]220955[/ATTACH]
I believe you can boot from the live CD in lower video mode by pressing one of the function keys. Maybe F6?

---

### Post by coffeecat on 2012-07-09
@lmart, to help you with the usb wireless device, we need the whole output that lsusb gives you. This:

> **lmart said:**
> 
USB Devices
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
	Microsoft® Nano Transceiver v2.0	
EHCI Host Controller
	[COLOR="Red"]Compact Wireless-G USB Adapter[/COLOR]

If that's from the output of lsusb, you've cropped out the most important bit - the ID number - without which we cannot identify the wireless chipset.

Please run "lsusb" from the terminal, highlight the whole of the output with the mouse, then right-click -> copy, and then paste it into your post. Post the output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by lmart on 2012-07-09
@coffeecat

thanks for your reply
previous output from another linux hardware id program
if there is anything else you would like me to do to help, please let me know

```

sh-4.1# lsusb                   
Bus 001 Device 001: ID 1d6b:0002
Bus 002 Device 001: ID 1d6b:0001
Bus 003 Device 001: ID 1d6b:0001
Bus 004 Device 001: ID 1d6b:0001
Bus 001 Device 004: ID 13b1:0020
Bus 002 Device 002: ID 045e:0745
Bus 002 Device 003: ID 045e:0745
sh-4.1# 

```

---

### Post by coffeecat on 2012-07-09
That's a strange lsusb output - a lot of it seems to be missing. Anyway, this line:

```
Bus 001 Device 004: ID 13b1:0020
```

Identifies your wireless USB device. According to this [Debian wiki page]("http://wiki.debian.org/WiFi/rt73"), that ID refers to:

> USB: 13B1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]

I would have thought that would have worked in 12.04, but I don't have any recent experience of Ralink wireless devices. Perhaps someone with experience of that device will be able to help you.

---

### Post by lmart on 2012-07-09
@coffeecat

Thanks. Copied the exact output from lsusb.
Assuming I wait until someone responds to my post, correct?

Assuming I have to load a driver, is there a tutorial that provides a step-by-step for the process? Never added a driver before.

---

### Post by wildmanne39 on 2012-07-10
Hi, please try:
```
sudo modprobe -r rt73usb
sudo modprobe rt73usb nohwcrypt=Y
```
Watch for errors.

If it does not come on post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
nm-tool
```
by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by lmart on 2012-07-10
@wildmanne39

Using the LiveCD, how do I get into the terminal to enter these commands?

---

### Post by irv on 2012-07-10
> **lmart said:**
> @wildmanne39

Using the LiveCD, how do I get into the terminal to enter these commands?
There should be an icon in the dash to launch the terminal. If not just hit the super key (windows key on the keyboard) and start typing terminal. When it shows up just click on the icon.
[ATTACH]221025[/ATTACH]   [ATTACH]221026[/ATTACH]

---

### Post by wildmanne39 on 2012-07-10
Hi, ctrl+alt+t.
Thanks

---

### Post by lmart on 2012-07-10
@irv & @wildmanne39
Thanks for your help getting me into terminal. Completely forgot about right-click on mouse.

@wildmanne39
thanks for your suggestions, fyi

1. my computer hung/froze on: sudo modprobe -r rt73usb
2. my access point: 398VC
3. completed your request (below); have absolutely no idea what these commands do, where can I go to learn?

```

xubuntu@xubuntu:~/Desktop$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
xubuntu@xubuntu:~/Desktop$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux xubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux
xubuntu@xubuntu:~/Desktop$ lspci -nnk | grep -iA2 net
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Trigem Computer Inc. Device [109f:3186]
	Kernel driver in use: 8139too
xubuntu@xubuntu:~/Desktop$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

xubuntu@xubuntu:~/Desktop$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
xubuntu@xubuntu:~/Desktop$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        00:18:39:0E:C7:9A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    bill:            Infra, 00:1F:33:46:B6:9D, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Wireless:        Infra, E8:39:DF:9F:01:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    398VC:           Infra, E8:39:DF:AA:C3:E5, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WEP
    VWAB9:           Infra, 00:24:D2:81:68:38, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WEP
    MOTOMESH:        Infra, 00:1A:DE:0D:3B:03, Freq 2412 MHz, Rate 54 Mb/s, Strength 50


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:40:2B:7E:E9:19

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


xubuntu@xubuntu:~/Desktop$ 


```

---

### Post by lmart on 2012-07-10
fyi, a notification pops up to let me know to connect to my wireless, it identifies my access point and requests the WEP key, enter the key, the arrows go around in circles for quite some time, then it requests the WEP key again, and the circle continues

---

### Post by wildmanne39 on 2012-07-10
Hi, which network are you try to connect too?

To learn about commands you can type man plus the name of the command into the terminal and it will tell you what the commands do.

After you ran the ```
sudo modprobe -r rt73usb
``` 
command did you run this one:
```
sudo modprobe rt73usb nohwcrypt=Y
```
Thanks

---

### Post by lmart on 2012-07-10
@wildmanne39
thanks, 398VC
didn't run the 2nd cmd as the 1st crashed
just ran sudo modprobe rt73usb nohwcrypt=Y nothing happened

---

### Post by wildmanne39 on 2012-07-10
Hi, what do you mean the first crashed? exact error message please and the commands are meant to be ran one after the other.

Which network are you try to connect too?
Thanks

---

### Post by lmart on 2012-07-10
@wildmanne39
thanks

**sudo modprobe -r rt73usb**
  this command caused my computer to freeze up, I had to turn it off then re-boot
**sudo modprobe rt73usb nohwcrypt=Y**
  this command simply returned to the command prompt

**no error message on either command**

Which network are you try to connect too? **398VC**

---

### Post by wildmanne39 on 2012-07-10
Hi, that may be because you are running ubuntu from a livecd I have never seen that happen before, also remember that a live cd runs slower it could have just needed more time.

I recommend going into your router settings and changing encryption to wpa2 only if you have that option because some linux drivers do not like wep very much.

You will also need to change your settings in network manager to wpa/wpa2 if it is setup for wep.
Thanks

---

