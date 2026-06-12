---
title: "Will this old wireless card work?"
date: 2009-04-05
forum: General Help
---

### Post by n000buntu on 2009-04-05
Hi, all! I am new (clearly) to Linux, and loving Ubuntu so far, but not too hip. I installed eeebuntu on my new ASUS netbook and it worked out of the box. Everything worked on my first-ever install of a Linux OS. So, yay!

I liked Ubuntu so much I just installed it on an old Dell PC. Rough guess, an 8 yr old Dell. It *was* running XP Home, and connecting to my linksys wireless network via a US Robotics PCI card which isn't as old as the computer, but still pretty old. My wireless network is unprotected, other than MAC filtering, and of course the router was configured to recognize the card by its MAC address under windows. 

I just finished installing 8.04 (it was just a free CD in an Ubuntu book I bought). The install went smoothly, but it's not detecting my wireless network anymore. In trying to make sure Ubuntu was seeing my card, I ran ifconfig -a, and I see a number that looks like the MAC address except it's followed by a bunch of extra "00:00:00:00."

Anyway, what am I missing? Will I need to buy a new wireless PCI card to get this working? Any ideas as to what else I might try?

Sorry this is so long, and I hope I provided all relevant details.

---

### Post by hardyn on 2009-04-05
because many wifi cards use closed source firmwares there is still dodgy native support for wifi under linux.  do you research to see if that card will work for you; if it didn't detect out of the box, you may be out of luck; although if you look past the USR label and see what chipset they were using you may be able to force a driver.

now there is always the NDISwrapper as well; i will let you read on that.

---

### Post by n000buntu on 2009-04-05
Thanks for the quick answer. After finding the thread on installing NDIS wrapper, which is 31 pages long (LOL), I am scared of NDIS wrapper. I have a feeling it might be easier to just scrounge up whatever PCI cards I can and start swapping them in and testing them...heh.

Alternatively, is there any reference I could consult which would name specific cards, that I could still purchase, which are known to work with Heron?

---

### Post by spcwingo on 2009-04-05
You can try booting with the card in and running from the terminal:

```
lspci
```

Post the output here and we might be able to help you get it going.  I see that you mentioned ndiswrapper.  It's not as bad as it sounds.  I don't know if anyone has told you, but there is a very simple GUI for ndiswrapper.  With the machine plugged in via ethernet open a terminal and enter this:

```
sudo apt-get install ndisgtk
```

This will install the GUI to ndiswrapper.  After install you can find it under system>admin>windows wireless drivers.  All you have to supply is the driver inf and sys files.  Simply place both in the same folder and in ndisgtk press new and navigate to the inf file.  You're wireless should now be working (you might have to reboot first, though).

---

### Post by n000buntu on 2009-04-06
Thanks for offering to help!  Here's the output from lspci:

> 00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:07.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
02:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:0a.0 USB Controller: OPTi Inc. 82C861 (rev 10)

And, in case it matters, the output from ifconfig -a:

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75500 (73.7 KB)  TX bytes:75500 (73.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:4e:39:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-4E-39-99-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Also, unfortunately, there is no ethernet port on the computer. I pulled the card out long ago to add something else.

---

### Post by kryptikos on 2009-04-06
She's seeing your card.
> 02:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) and > wlan0 Link encap:Ethernet HWaddr 00:1c:df:4e:39:99  show you that, that's the good news. All you need to do is obtain the driver for the 4318 card. With my AirForce One cards I've used the bcm-fwcutter firmware to bring my card online.
Although these threads are a little older they still stand.  

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear")

If you would still like to use the Ndiswrapper method this is a good instruction set:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Hopefully this will steer you in the right direction

---

### Post by n000buntu on 2009-04-06
Thanks! I will check out that stuff this afternoon and see where I get. :)

---

### Post by n000buntu on 2009-04-15
Just bought a Belkin wireless G card from eBay for $5. Slapped it in and it works perfectly. FTW.

---

### Post by paradigm2 on 2009-04-15
> **n000buntu said:**
> Just bought a Belkin wireless G card from eBay for $5. Slapped it in and it works perfectly. FTW.

I was surprised that both of my atheros based wifi cards (one is a linksys wmp110 v1.0 b/g/n) worked with zero configuration right after the jaunty 9.04 install -- and using wpa2-personal with AES no less!

WIFI support has came a long way in linux, this is for sure.

For the people who say to use ndiswrapper, after hearing that you have to re-install the driver after every kernel upgrade, i can't help but think one might be better off just getting a adapter which is better supported.

---

### Post by n000buntu on 2009-04-15
> **paradigm2 said:**
> 
For the people who say to use ndiswrapper, after hearing that you have to re-install the driver after every kernel upgrade, i can't help but think one might be better off just getting a adapter which is better supported.
That was my thought after reading a couple of NDISwrapper threads. A little scary for a n00b like me. :)

---

