---
title: "Wireless driver for Inspiron 2200"
date: 2009-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nyhus on 2009-06-21
Hi.

I'd like to start off saying I am new to ubuntu. Never used in my life. Dont know where anything is or how anything works.

Now to my problem:
A friend of mine talked me in to installing xubuntu on a old laptop of mine so that i can use it when my new one gets fixed. The problem is that i cant get the wireless network adapter to work. The only thing i could think of was to hit "fn" and "f2" to acctivate the adapter, but that worked bad. Therefor I've been googeling to see if i can find a working driver(not that i know how to install one in xubuntu) to get the **** train going. But thats not going too well.

Any one who know how i can fix this, I'd appreciate the help!

Btw, how do i start up a terminal?

---

### Post by ugm6hr on 2009-06-21
Look in the Menus for something called Terminal.

Then help us to help you by including some details:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by Nyhus on 2009-06-21
Ah, sorry, i'll try again:
> 1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.Wireless router, adsl.

> 2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).When i plottet in the lspci command, lots of stuff showed up. 
```
On network controller: Broadcom Corporation BCM4318 [Airforce One 54g) 802.11g Wireless LAN Controller (rev 02).
```When i plot lshw -class network this is what it says(some of it at least):
```
Configuration: broadcast = yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency 64 maxlatency=54 mingnt=8 module=e100 multicast=yes
*-network:0 DISABLED
Description: wireless interface
physical id:1
logical name: wlan0
capabilities: ethernet physical wireless
configuration: boadcast=yes multicast=yeas wireless=IEEE 802.11bg
*network:1 DISABLED
description: ethernet interface
```then it goes on with the same stuff there were above, with description, physical id, capabilities and configuration.

> 3. Who is your Internet Service Provider (and in which country)?Not quite sure, its my landlords wireless. He deals with the internet provider. Norway.

> 4. Which version of Ubuntu are you using?  e.g. Ubuntu 8.04, Xubuntu 7.10 etc and 32- vs 64-bit.When i plot in uname -a this comes up:
```
Linux xubuntu-laptop 2.6.27.7generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 Gnu/Linux

When i plot inlsb_release -a this comes up:
No LSB modules are avaible.
Distributor ID: Ubuntu
Description: Ubuntu 8.10
Release; 8.10
Codename: intrepid
```> 5. Can you get online with any other method?  e.g. if you have a wifi problem, can you connect with ethernet?No i cannot. When i hit the networksicon in xubuntu both networking and wireless is checked off,  but i cant choose eiter "wired network" or "wireless networks". So i cant scan for any wlans.

> 6. How are you getting online to post on this forum?I have a couple of other Windows-computers that works fine.

> 7. Include the **output** from the following commands from Terminal (all **case sensitive**). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.on ifconfig the much of same pops up as when i tryed the lsh class network command.

iwconfig:
```
wlan0 IEEE 802.11g ESSID: ""
         mode:Managed  Frequency: 2.423  Acess Point: Not-Associated
         Tx-Power: 27 dBm
         retyr min limit:7  RTS thr:off  Fragment thr=2352 B
         Link quality:0 Signal Level: 0 Noise level:0
         Rx invalid invalid nwid:0  Rx invalid crypt: 0 Rx invalid frag:0
         Tx excessiv retires:0  invalid misc:0  missed beacon:0

pan 0  no wireless extensions.
```When i tried to pin 208.67.219.101 i get the message:
connect: Network is unreachable

When i punch in [www.opendns.com]("http://www.opendns.com"), i get "unknow host www.opendns.com"

> 9. Do you dual-boot with Windows? No, when I installed xubuntu i cleaned out the disk completely.  


As i said in my first post, I havent tried much, cause I've never used ubuntu or any kind linux before. All I've done is check the "Hardware drivers" on the applications meny. Thats about it. I've googled a lot, but didnt get any further.

Edit:
Btw, i've plottet inn all the codes manually, so if theres anything wrong with the codes, tell me and i'll try again. For some reason the text program in xubuntu wont let me save files to my usbmemorything(i dont know what it's called in english :| )

---

### Post by ugm6hr on 2009-06-21
Your wifi card: Broadcom Corporation BCM4318 [Airforce One 54g)

You need the firmware to get this to work.  If you could connect your computer to the ADSL router with a cable, this would be a lot easier.  However, if you have to use your landlords, it may not be simple to trail a cable through his / her house.

So...  If I remember correctly:

You need:
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

PS: Is there a reason you chose 8.10 rather than 9.04?

This might be useful:
[http://ubuntuforums.org/showpost.php?p=5422091&postcount=2](http://ubuntuforums.org/showpost.php?p=5422091&postcount=2)
[http://linuxwireless.org/en/users/Drivers/b43#device_firmware](http://linuxwireless.org/en/users/Drivers/b43#device_firmware)

[COLOR="Red"]**EDIT:**[/COLOR]
This is probably your best bet if you don't have wired internet - it is a complete guide for Intrepid:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by Nyhus on 2009-06-21
Thanks, ill try it out.

> PS: Is there a reason you chose 8.10 rather than 9.04?
I downloaded the newest version of xubuntu i could find on the norwegian ubuntu-site. You think the adapter would work if i get a newer version? Or would i still need to do all this stuff?

---

### Post by Nyhus on 2009-06-21
Hey, thanks man, now it seems to work! Thank you so much, your a life saver :)

---

### Post by ugm6hr on 2009-06-21
> **Nyhus said:**
> I downloaded the newest version of xubuntu i could find on the norwegian ubuntu-site. You think the adapter would work if i get a newer version? Or would i still need to do all this stuff?

The main xubuntu site is probably a better place to get it from.

Nevertheless, you would still need to download the driver and install it as you have done in 9.04 (your wifi card is not supported "out-of-the-box" but will automatically install the driver if you connect via a wired connection).

9.04 has some issues with graphics drivers on Intel etc, but is generally a much nicer experience.

Enjoy.

---

